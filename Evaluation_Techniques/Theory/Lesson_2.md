# <span style="color:#2E86C1"><b>Data Leakage in Machine Learning</b></span>

**Data leakage** occurs when **information that should not be available at prediction time is used during model training**, causing the model to learn patterns that will not exist in real-world inference.

This leads to **artificially high performance metrics** (e.g., R², accuracy) but **poor performance in production**.

---

# <span style="color:#2E86C1"><b>1. Causality Perspective of Data Leakage</b></span>

Data leakage is fundamentally a **causality violation**.

In real-world prediction systems:

```text
Past information → Model → Prediction
```

But with leakage, the model accidentally learns:

```text
Future information → Model → Prediction
```

This breaks the **temporal or causal relationship**.

Example loan model:

```text
Input Features → sanction_amount
```

If a feature indirectly contains information about the **final sanctioned amount**, the model is cheating.

Example leakage feature:

```text
approved_limit
final_loan_amount
```

These are **post-decision variables**.

So the model learns:

```text
approved_limit ≈ sanction_amount
```

Result:

```text
R² ≈ 0.99
```

But in production those features **will not exist before prediction**.

---

# <span style="color:#2E86C1"><b>2. Effect of Data Leakage on Model</b></span>

Data leakage causes several serious problems.

### Artificially high evaluation scores

Example:

```text
Train R² = 0.99
Test R² = 0.98
```

Looks excellent but is misleading.

---

### Poor real-world performance

In production:

```text
Production R² = 0.50
```

because the leaked information is no longer available.

---

### Incorrect feature importance

The model incorrectly identifies leakage features as highly important.

Example:

| Feature        | Importance |
| -------------- | ---------- |
| approved_limit | 0.82       |
| credit_score   | 0.05       |

This misleads feature engineering decisions.

---

### Model overfitting to artifacts

The model learns **dataset artifacts rather than true relationships**.

---

# <span style="color:#2E86C1"><b>3. Types of Data Leakage</b></span>

## Target Leakage

The feature directly or indirectly contains information about the target.

Example:

```text
Target → sanction_amount
Feature → approved_limit
```

Approved limit is calculated after the loan decision.

---

## Temporal Leakage

Using future information to predict past events.

Example fraud detection:

```text
Transaction features
+
chargeback indicator
```

But chargeback happens **weeks later**.

---

## Train-Test Leakage

Information from test set leaks into training.

Example mistake:

```python
scaler.fit(X)
X_scaled = scaler.transform(X)
train_test_split(...)
```

Here the scaler **saw the test data**.

Correct workflow:

```python
train_test_split
fit scaler on training data
transform train and test
```

---

## Cross Validation Leakage

Occurs when preprocessing is applied **before cross-validation**.

Example mistake:

```python
imputer.fit(X)
cross_val_score(model, X)
```

Correct approach:

Use pipelines.

```python
Pipeline([
    ("imputer", SimpleImputer()),
    ("model", RandomForestRegressor())
])
```

---

# <span style="color:#2E86C1"><b>4. How to Detect Data Leakage</b></span>

### Suspiciously high performance

Example:

```text
R² > 0.98
Accuracy > 99%
```

on messy real-world data.

---

### Extremely high feature correlation

Check:

```python
df.corr()[target]
```

If:

```text
|corr| > 0.95
```

investigate the feature.

---

### Unrealistic features

Ask:

```text
Would this feature be available before prediction?
```

If not → leakage.

---

# <span style="color:#2E86C1"><b>5. Techniques to Prevent Data Leakage</b></span>

## Proper Train-Test Split

Always split data **before preprocessing**.

Correct order:

```text
Dataset
↓
Train-Test Split
↓
Preprocessing
↓
Model Training
```

---

## Use Pipelines

Using **scikit-learn** pipelines prevents leakage.

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

Now scaling is performed **inside cross validation folds**.

---

## Time-Based Splitting

For temporal data:

Use chronological split.

Example:

```text
2019-2022 → training
2023 → testing
```

Not random split.

---

## Feature Auditing

For each feature ask:

```text
Is this feature available at prediction time?
```

If no → remove.

---

## Feature Lineage Tracking

Track how features are generated.

Example:

```text
loan_limit_ratio = sanctioned_amount / income
```

This leaks the target.

---

# <span style="color:#2E86C1"><b>6. When to Use Each Prevention Method</b></span>

| Scenario                   | Prevention Technique         |
| -------------------------- | ---------------------------- |
| Tabular dataset            | Train-test split + pipelines |
| Time-series data           | Time-based split             |
| Financial datasets         | Strict feature auditing      |
| Large ML pipelines         | Feature stores               |
| Cross validation workflows | Pipelines                    |

---

# <span style="color:#2E86C1"><b>7. Real Example in Loan Models</b></span>

Suppose you predict:

```text
sanction_amount
```

Potential leakage features:

```text
approved_limit
loan_disbursed_amount
emi
interest_amount
```

These are **downstream outcomes**.

Correct features:

```text
income
credit_score
debt_ratio
gst_turnover
repayment_history
```

These exist **before the decision**.

---

# <span style="color:#2E86C1"><b>8. Practical Workflow to Avoid Leakage</b></span>

Professional ML workflow:

```text
Raw dataset
↓
Feature audit
↓
Train-test split
↓
Pipeline preprocessing
↓
Cross validation
↓
Model training
↓
Evaluation
```

---

# <span style="color:#2E86C1"><b>Key Insight</b></span>

Data leakage occurs when the model learns **information from the future or the target itself**.

The fundamental rule:

```text
A model must only use information available at prediction time.
```

Any violation of this rule leads to **data leakage**.

---

If you want, I can also show you **5 subtle leakage patterns that even experienced ML engineers miss**, especially in **financial datasets like loan approval and credit scoring**.
