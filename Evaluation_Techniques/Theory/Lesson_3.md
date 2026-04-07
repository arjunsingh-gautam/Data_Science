#<span style="color:#2E86C1"><b>How Data Leakage Happens Without Pipelines (Step-by-Step)</b></span>

When preprocessing steps (scaling, imputation, encoding, feature selection) are done **outside a pipeline**, they are often applied **before splitting or before cross-validation**.

This causes **information from the test set to influence the training process**, which is **data leakage**.

We will walk through **exactly how leakage happens step by step**.

---

# <span style="color:#2E86C1"><b>1. Example Dataset</b></span>

Suppose you are predicting:

```text
target → sanction_amount
```

Features:

| income | credit_score | debt_ratio | sanction_amount |
| ------ | ------------ | ---------- | --------------- |
| 50000  | 700          | 0.2        | 30000           |
| 60000  | 720          | 0.25       | 35000           |
| 70000  | 750          | 0.3        | 40000           |
| 80000  | 780          | 0.35       | 45000           |

---

# <span style="color:#2E86C1"><b>2. Incorrect Workflow (No Pipeline)</b></span>

Many beginners do this:

```python
from sklearn.preprocessing import StandardScaler
from sklearn.model_selection import train_test_split
```

### Step 1 — Scale Entire Dataset

```python
scaler = StandardScaler()

X_scaled = scaler.fit_transform(X)
```

Problem:

```text
scaler.fit() uses statistics from ALL DATA
```

Which includes:

```text
train data
+
test data
```

---

### Step 2 — Train-Test Split

```python
X_train, X_test, y_train, y_test = train_test_split(X_scaled, y)
```

Now the training data has already been influenced by **test set statistics**.

This is **data leakage**.

---

# <span style="color:#2E86C1"><b>3. Why This Is Leakage</b></span>

Scaling computes:

```text
mean
standard deviation
```

Example dataset:

| income |
| ------ |
| 50000  |
| 60000  |
| 70000  |
| 80000  |

Mean:

```text
65000
```

If the test sample contains:

```text
80000
```

then the mean calculation already **includes that test information**.

So the model indirectly knows something about the test set distribution.

This improves evaluation artificially.

---

# <span style="color:#2E86C1"><b>4. Correct Workflow (Using Pipeline)</b></span>

Correct order:

```text
Dataset
↓
Train-Test Split
↓
Fit preprocessing on training data only
↓
Transform test data
↓
Train model
```

Example:

```python
X_train, X_test, y_train, y_test = train_test_split(X, y)

scaler = StandardScaler()

X_train_scaled = scaler.fit_transform(X_train)
X_test_scaled = scaler.transform(X_test)
```

Now:

```text
mean and std computed only from training data
```

The test data remains unseen.

---

# <span style="color:#2E86C1"><b>5. Leakage Becomes Worse with Cross Validation</b></span>

Suppose we run **cross validation**.

Example folds:

```text
Fold1
Fold2
Fold3
Fold4
Fold5
```

If preprocessing is done before CV:

```python
scaler.fit(X)
cross_val_score(model, X_scaled, y)
```

Then:

```text
Each fold already contains information from the other folds
```

Example:

When evaluating fold 1:

```text
Training → Fold2 Fold3 Fold4 Fold5
Test → Fold1
```

But the scaler was fit on:

```text
Fold1 Fold2 Fold3 Fold4 Fold5
```

So fold1 statistics leaked.

---

# <span style="color:#2E86C1"><b>6. Correct Solution Using Pipelines</b></span>

Using **scikit-learn** pipelines prevents this.

Example:

```python
from sklearn.pipeline import Pipeline
from sklearn.preprocessing import StandardScaler
from sklearn.ensemble import RandomForestRegressor

pipeline = Pipeline([
    ("scaler", StandardScaler()),
    ("model", RandomForestRegressor())
])
```

Now during cross validation:

```python
cross_val_score(pipeline, X, y, cv=5)
```

What happens internally:

```text
Fold 1
fit scaler on training folds
transform training folds
transform test fold
train model
evaluate
```

Then repeated for all folds.

Each fold remains **isolated**.

---

# <span style="color:#2E86C1"><b>7. Other Preprocessing Steps That Cause Leakage</b></span>

Leakage can occur in many preprocessing operations.

### Imputation

Incorrect:

```python
imputer.fit(X)
```

Correct:

```python
imputer.fit(X_train)
```

---

### Feature Selection

Incorrect:

```python
selector.fit(X, y)
```

Correct:

```python
selector.fit(X_train, y_train)
```

---

### PCA

Incorrect:

```python
pca.fit(X)
```

Correct:

```python
pca.fit(X_train)
```

---

# <span style="color:#2E86C1"><b>8. Visualizing Leakage</b></span>

Without pipeline:

```text
Dataset
↓
Preprocessing (fit on entire dataset)
↓
Train-test split
↓
Model training
```

Leakage occurs here.

---

With pipeline:

```text
Dataset
↓
Train-test split
↓
Pipeline
   ↓
fit preprocessing on train
   ↓
train model
```

Now test data remains unseen.

---

# <span style="color:#2E86C1"><b>9. Real Impact of Leakage</b></span>

Example results.

Without pipeline:

```text
R² = 0.98
```

With correct pipeline:

```text
R² = 0.86
```

The previous performance was **inflated**.

---

# <span style="color:#2E86C1"><b>Key Insight</b></span>

Leakage happens when **test data influences preprocessing statistics used during training**.

The rule is:

```text
No step in the training pipeline should ever see the test data.
```

Pipelines enforce this rule automatically.

---

If you'd like, I can also explain **one extremely subtle leakage pattern that often happens in financial ML datasets (like loan sanction models)** which can produce **R² ≈ 0.99 even when pipelines are used correctly.**
