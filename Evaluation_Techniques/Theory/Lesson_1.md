# <span style="color:#2E86C1"><b> Cross Validation in Machine Learning</b></span>

**Cross validation** is a model evaluation technique used to measure **how well a machine learning model generalizes to unseen data**.

Instead of evaluating a model using **one train-test split**, cross validation **repeatedly trains and tests the model on different parts of the dataset**.

This gives a **more reliable estimate of model performance**.

---

# <span style="color:#2E86C1"><b>1. Why Cross Validation Is Needed</b></span>

Suppose you split data once:

```text
Dataset
   ↓
Train (80%)
Test (20%)
```

Then train a model:

Example:

```
R² = 0.98
```

Problem:

The result depends **heavily on how the dataset was split**.

A different split might produce:

```
R² = 0.91
```

So a single split can give **unstable evaluation**.

Cross validation solves this.

---

# <span style="color:#2E86C1"><b>2. Idea Behind Cross Validation</b></span>

Instead of one train-test split, we create **multiple splits**.

The model is trained **multiple times**.

Example:

```
Dataset → split into k parts
```

Each part is used **once as test data**.

---

# <span style="color:#2E86C1"><b>3. K-Fold Cross Validation</b></span>

The most common method is **K-Fold Cross Validation**.

Example with **k = 5**:

Dataset is split into **5 equal parts**.

```
Fold1 Fold2 Fold3 Fold4 Fold5
```

---

### Iteration 1

```
Train: Fold2 Fold3 Fold4 Fold5
Test : Fold1
```

---

### Iteration 2

```
Train: Fold1 Fold3 Fold4 Fold5
Test : Fold2
```

---

### Iteration 3

```
Train: Fold1 Fold2 Fold4 Fold5
Test : Fold3
```

---

### Iteration 4

```
Train: Fold1 Fold2 Fold3 Fold5
Test : Fold4
```

---

### Iteration 5

```
Train: Fold1 Fold2 Fold3 Fold4
Test : Fold5
```

Now we get **5 performance scores**.

Example:

```
R² scores:
0.97
0.98
0.96
0.97
0.98
```

Final evaluation:

```
Mean R² = 0.972
```

This is much **more reliable**.

---

# <span style="color:#2E86C1"><b>4. Implementation in scikit-learn</b></span>

Using **scikit-learn**:

```python
from sklearn.model_selection import cross_val_score
from sklearn.ensemble import RandomForestRegressor

model = RandomForestRegressor()

scores = cross_val_score(model, X, y, cv=5, scoring="r2")

print(scores)
print(scores.mean())
```

Example output:

```
[0.97, 0.98, 0.96, 0.97, 0.98]

Mean R² = 0.972
```

---

# <span style="color:#2E86C1"><b>5. Advantages of Cross Validation</b></span>

### Better performance estimation

Uses **multiple train-test splits**.

---

### Reduces variance

Evaluation is less dependent on a single random split.

---

### Efficient use of data

Every sample becomes **test data once** and **training data multiple times**.

---

### Helps detect overfitting

If training score is much higher than CV score:

```
Train R² = 0.99
CV R² = 0.85
```

Model is likely overfitting.

---

# <span style="color:#2E86C1"><b>6. Choosing the Value of K</b></span>

Common choices:

| K   | Usage           |
| --- | --------------- |
| 3   | fast evaluation |
| 5   | standard choice |
| 10  | very reliable   |

Most ML workflows use:

```
k = 5 or 10
```

---

# <span style="color:#2E86C1"><b>7. Cross Validation vs Train-Test Split</b></span>

| Method           | Reliability |
| ---------------- | ----------- |
| Train-test split | Low         |
| Cross validation | High        |

Train-test split is often used for:

```
final model evaluation
```

Cross validation is used for:

```
model selection
hyperparameter tuning
```

---

# <span style="color:#2E86C1"><b>8. Cross Validation in Hyperparameter Tuning</b></span>

Cross validation is also used inside **GridSearchCV**.

Example:

```
RandomForest with different parameters
```

Each parameter configuration is evaluated using cross validation.

---

# <span style="color:#2E86C1"><b>9. Important Intuition</b></span>

Think of cross validation as **repeating the experiment multiple times**.

Instead of trusting **one experiment**, we average many experiments.

```
Single split → one opinion
Cross validation → consensus
```

---

# <span style="color:#2E86C1"><b>10. Example Workflow for Your Loan Model</b></span>

For your **sanction amount prediction model**:

```
Dataset
   ↓
Feature engineering
   ↓
Cross validation
   ↓
Compare models
   ↓
Select best model
```

Example code:

```python
from sklearn.model_selection import cross_val_score
from sklearn.ensemble import RandomForestRegressor

model = RandomForestRegressor(n_estimators=300)

scores = cross_val_score(model, X, y, cv=5, scoring="r2")

print("CV R2:", scores.mean())
```

---

# <span style="color:#2E86C1"><b>Key Insight</b></span>

Cross validation answers the question:

```
How well will my model perform on completely unseen data?
```

It is **one of the most important tools in machine learning model evaluation**.

---

If you'd like, I can also explain **a very critical mistake many ML engineers make with cross validation in financial datasets (like loan data)** — it can silently introduce **data leakage and inflated R² scores.**
