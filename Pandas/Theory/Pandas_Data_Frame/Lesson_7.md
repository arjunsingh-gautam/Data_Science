# <span style="color:yellow">**Handling Missing Values**</span>

# How to handle missing values in a dataset using **Pandas** — complete guide

Below is a practical, decision-oriented guide covering **all common techniques** (and some advanced ones), **how to use them**, **when** to use each, **code examples**, **best practices** and **precautions**.

---

# 1) Quick workflow (recommended)

1. **Detect & quantify** missingness.
2. **Explore pattern** (MCAR / MAR / MNAR).
3. **Decide strategy** per column (drop / impute / flag).
4. **Implement** (in a reproducible pipeline).
5. **Validate** (compare distributions, model performance, or simulate masking).

---

# 2) Detect & quantify missing values

```python
import pandas as pd
df.isnull().sum()            # count per column
df.isnull().mean().sort_values(ascending=False)  # fraction missing per column
df.isnull().sum().sum()      # total missing values
```

Visual checks: `df.head()`, `df.info()`, and plotting missingness (e.g., seaborn/missingno) help spot patterns.

---

# 3) Understand missingness mechanism (conceptual)

* **MCAR** — Missing Completely At Random: missing independent of data. Imputation simpler.
* **MAR** — Missing At Random: missing depends on observed data → use model-based/group imputation.
* **MNAR** — Missing Not At Random: missing depends on unobserved values → trickiest; consider modeling missingness explicitly or domain solutions.

You can test/inspect correlations between `.isnull()` and other variables to get a hint.

---

# 4) Strategies & techniques (with when to use, code + examples)

## A — **Dropping**

### 1. Drop rows with any NaN

Use when only a few rows are missing or target variable missing.

```python
df_clean = df.dropna(axis=0)        # drop any row with at least one NaN
```

### 2. Drop rows/cols by threshold

Drop columns with too many NaNs or rows with many NaNs.

```python
df.dropna(axis=1, thresh=int(0.5*len(df)))  # keep cols with >=50% non-NaN
df.dropna(axis=0, thresh=2)                 # keep rows with at least 2 non-NaNs
```

**When to use:** When missingness is small or column is useless (> e.g. 50–80% missing).
**Precaution:** dropping may bias dataset and reduce sample size.

---

## B — **Simple imputation (single-value)**

### 1. Constant value

Good for categorical columns or if you want explicit "missing" category.

```python
df['cat'] = df['cat'].fillna('Missing')
df['num'] = df['num'].fillna(0)   # or some sentinel
```

### 2. Mean / Median / Mode

Numeric columns: mean (symmetric), median (skewed), mode (categorical).

```python
df['num'] = df['num'].fillna(df['num'].mean())
df['num'] = df['num'].fillna(df['num'].median())
df['cat'] = df['cat'].fillna(df['cat'].mode()[0])
```

**When to use:** quick baseline, small fraction missing, or features where mean/median is sensible.
**Precautions:** mean imputation reduces variance and can bias correlations.

---

## C — **Forward/Backward Fill (time-series / ordered data)**

```python
df['value'] = df['value'].ffill()  # forward fill
df['value'] = df['value'].bfill()  # backward fill
# limit how many consecutive fills:
df['value'].ffill(limit=1)
```

**When to use:** sensor/time-series or ordered logs where last valid observation is a good proxy.
**Precautions:** don't use if order is meaningless.

---

## D — **Interpolation**

Numeric interpolation methods: linear, time-based, polynomial, spline.

```python
# index must be datetime for method='time'
df = df.set_index('timestamp')
df['value'].interpolate(method='linear')
df['value'].interpolate(method='time')
df['value'].interpolate(method='polynomial', order=2)
```

**When:** time-series with reasonably continuous values.
**Precaution:** interpolation can create unrealistic values if gaps are large.

---

## E — **Group-wise imputation (conditional)**

Fill missing by group statistics (mean/median/mode within group).

```python
# fill with group mean:
df['num'] = df.groupby('group')['num'].transform(lambda x: x.fillna(x.mean()))
# or using .apply:
df['num'] = df['num'].fillna(df.groupby('group')['num'].transform('median'))
```

**When:** missing depends on group (e.g., fill salary by department). Good for MAR.

---

## F — **Indicator / Flag variable**

Add a boolean column to indicate missingness — often helpful for model to learn missingness pattern.

```python
df['num_missing'] = df['num'].isnull().astype(int)
df['num'] = df['num'].fillna(df['num'].median())
```

**When:** MNAR or when missingness itself carries information.

---

## G — **Hot-deck (donor-based) and random sampling**

Impute missing value with a randomly selected observed value from the same column or group — preserves distribution.

```python
import numpy as np
vals = df['num'].dropna().values
df.loc[df['num'].isnull(), 'num'] = np.random.choice(vals, size=df['num'].isnull().sum())
```

**When:** want to preserve distribution and variance; stochastic.
**Precaution:** introduces randomness (use seed for reproducibility).

---

## H — **Model-based single imputation**

Predict missing values with a model using other features. Example with `sklearn`'s `SimpleImputer`, `KNNImputer`, or `IterativeImputer`.

### `SimpleImputer` (sklearn) — mean/median/most\_frequent/constant

```python
from sklearn.impute import SimpleImputer
imp = SimpleImputer(strategy='median')
df_num = pd.DataFrame(imp.fit_transform(df[['num1','num2']]), columns=['num1','num2'])
```

### `KNNImputer`

```python
from sklearn.impute import KNNImputer
imp = KNNImputer(n_neighbors=5)
df_imp = pd.DataFrame(imp.fit_transform(df_num), columns=df_num.columns)
```

### `IterativeImputer` (MICE-like, multivariate)

```python
from sklearn.experimental import enable_iterative_imputer  # may be needed
from sklearn.impute import IterativeImputer
imp = IterativeImputer(random_state=0)
df_imp = pd.DataFrame(imp.fit_transform(df_num), columns=df_num.columns)
```

**When:** complex multivariate relationships exist (MAR). `IterativeImputer` / MICE are strong but heavier.
**Precautions:** beware of leakage (fit on training only), computationally expensive.

---

## I — **Multiple Imputation**

Perform several imputations to capture uncertainty (MICE iterations), then combine analysis results. Useful for uncertainty quantification. In Python you can use `statsmodels.imputation` or `fancyimpute` or `sklearn`'s `IterativeImputer` (with different seeds) — more advanced.

---

## J — **Categorical columns — special handling**

* Add `'Missing'` category: `df['cat'] = df['cat'].fillna('Missing')`
* Use mode per group: `df.groupby('group')['cat'].apply(lambda x: x.fillna(x.mode()[0] if len(x.mode())>0 else 'Missing'))`
* Convert to `category` dtype to save memory: `df['cat'] = df['cat'].astype('category')`

**When:** categorical with informative missingness or many categories.

---

## K — **Target variable missing**

If target (y) has missing values:

* Usually drop those rows for supervised learning (unless performing semi-supervised learning or specialized modeling).

---

# 5) Pipelines & avoiding data leakage (very important)

Always fit imputation on **training** data and **apply** to validation/test. Use `sklearn.pipeline.Pipeline` and `ColumnTransformer` for different imputers per column type.

```python
from sklearn.pipeline import Pipeline
from sklearn.impute import SimpleImputer
from sklearn.compose import ColumnTransformer
from sklearn.preprocessing import StandardScaler

num_cols = ['num1','num2']
cat_cols = ['cat1']

num_pipe = Pipeline([('imputer', SimpleImputer(strategy='median')),
                     ('scaler', StandardScaler())])
cat_pipe = Pipeline([('imputer', SimpleImputer(strategy='constant', fill_value='Missing'))])

preprocessor = ColumnTransformer([
    ('num', num_pipe, num_cols),
    ('cat', cat_pipe, cat_cols)
])
# Then use with estimator pipeline: Pipeline([('preproc', preprocessor), ('model', clf)])
```

**When:** always in ML workflows — prevents test leakage.

---

# 6) Validate imputation choices

* **Distribution check:** compare histograms before/after (or imputed vs original non-missing).
* **Model comparison:** compare model metrics (CV) using different imputations.
* **Simulation:** artificially mask known values and compare imputations (compute RMSE).
* **Stability:** check effect on correlations and relationships.

---

# 7) Practical rules / Best practices & precautions

**Best practices**

* Inspect missingness patterns (`df.isna().sum()`, heatmap).
* Use domain knowledge — sometimes a missing value means a category (e.g., no purchase).
* Add a **missing indicator** column when missingness may be informative.
* Use `groupby(...).transform()` for group-wise imputation.
* Use pipelines to avoid leakage and ensure reproducibility.
* Prefer median over mean for skewed numeric data.
* For time series prefer `ffill`/`bfill` or time interpolation.
* For high-cardinality categorical columns, consider dropping or advanced encoding instead of naive fill.

**Precautions**

* **Do not** impute using any information from the test set (no leakage).
* Mean/median imputation reduces variance and biases.
* Imputation can change relationships and correlations — monitor downstream effects.
* Beware of dtype changes after `fillna` (e.g., ints → floats if NaN inserted). Cast back if needed.
* Using `inplace=True` can make code less readable and prevent reproducibility; prefer assignment.

---

# 8) Example: small end-to-end demonstration (conceptual code)

```python
# 1. detect
print(df.isnull().mean().sort_values(ascending=False))

# 2. simple rule
# drop cols with >60% missing
cols_to_drop = df.columns[df.isnull().mean() > 0.6]
df = df.drop(columns=cols_to_drop)

# 3. create missing flags
for c in ['age','income']:
    df[c + '_missing'] = df[c].isnull().astype(int)

# 4. numeric imputation by group
df['income'] = df.groupby('occupation')['income'].transform(lambda x: x.fillna(x.median()))

# 5. categorical fill
df['city'] = df['city'].fillna('Missing')

# 6. fallback for remaining numeric NaN with global median
df['age'] = df['age'].fillna(df['age'].median())

# 7. pipeline for ML (fit on train only!)
```

---

# 9) Quick decision cheat-sheet: which technique to use?

* **Tiny fraction missing (<1–5%)** → consider dropping rows.
* **Column has huge missingness (>50–80%)** → drop column (unless critical).
* **Numeric symmetric distribution** → mean/median imputation.
* **Numeric skewed** → median or model-based.
* **Time-series** → ffill / interpolate.
* **Categorical** → mode or new category `'Missing'`.
* **MAR** (depends on other observed features) → group-based / model-based / IterativeImputer.
* **MNAR** → consider indicator + domain solution; multiple imputation or explicit modeling of missingness.

---

# 10) Final tips

* Reproducibility: set random seeds for stochastic methods.
* Use `df.info()` & `df.describe()` after imputation to sanity-check datatypes and ranges.
* Log your decisions — for audits and reproducibility.
* When in doubt, test multiple strategies and choose the one that gives the best validation performance and preserves domain plausibility.

---


