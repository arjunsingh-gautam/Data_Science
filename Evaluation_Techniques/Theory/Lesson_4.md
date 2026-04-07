# <span style="color:#2E86C1"><b>Cross Validation — Causality and the Problem It Solves</b></span>

Cross validation is a model evaluation method used to **estimate how well a machine learning model will perform on unseen data**.

To understand it deeply, we should analyze two aspects:

1. **Its causal reasoning**
2. **The fundamental problem it solves**

---

# <span style="color:#2E86C1"><b>1. The Core Problem in Machine Learning Evaluation</b></span>

In supervised learning, we train a model to learn a function:

```text
X → y
```

Where:

```
X = features
y = target
```

The model learns from **training data**, but the real goal is to predict **future unseen data**.

The problem:

```text
We only have one dataset.
```

But we want to estimate:

```text
How the model performs on unknown future data.
```

This creates a **generalization problem**.

---

# <span style="color:#2E86C1"><b>2. The Causal Structure of Machine Learning</b></span>

In the real world, the causal process is:

```text
Data generation process
        ↓
Historical dataset
        ↓
Model training
        ↓
Future predictions
```

The model must learn patterns that **generalize to future data drawn from the same distribution**.

However, we do not have access to future data.

So we simulate it.

---

# <span style="color:#2E86C1"><b>3. Why a Single Train-Test Split Is Unstable</b></span>

A common approach:

```text
Dataset
   ↓
Train (80%)
Test (20%)
```

The model trains on 80% and evaluates on 20%.

Problem:

```text
Performance depends heavily on which samples fall into the test set.
```

Example:

Split A:

```
R² = 0.91
```

Split B:

```
R² = 0.84
```

Different splits produce **different evaluations**.

This introduces **sampling variance**.

---

# <span style="color:#2E86C1"><b>4. What Cross Validation Does</b></span>

Cross validation solves the instability problem by **repeating the evaluation multiple times using different test sets**.

Example with **5-fold cross validation**:

```text
Dataset → split into 5 folds
```

Each fold becomes the test set once.

Iteration structure:

```
Iteration 1
Train → Fold2 Fold3 Fold4 Fold5
Test  → Fold1

Iteration 2
Train → Fold1 Fold3 Fold4 Fold5
Test  → Fold2

Iteration 3
Train → Fold1 Fold2 Fold4 Fold5
Test  → Fold3

Iteration 4
Train → Fold1 Fold2 Fold3 Fold5
Test  → Fold4

Iteration 5
Train → Fold1 Fold2 Fold3 Fold4
Test  → Fold5
```

Now we obtain multiple performance scores.

Example:

```
0.92
0.90
0.91
0.89
0.93
```

Final evaluation:

```
Mean performance ≈ 0.91
```

This is a **much more reliable estimate**.

---

# <span style="color:#2E86C1"><b>5. The Causal Interpretation of Cross Validation</b></span>

Cross validation simulates the causal scenario:

```text
Train on past data
Test on unseen data
```

But instead of doing this once, we simulate it **multiple times**.

Conceptually:

```
Dataset
↓
Multiple alternate histories
↓
Train/test simulation
↓
Average performance
```

This approximates **expected performance on future samples**.

---

# <span style="color:#2E86C1"><b>6. The Statistical Problem Cross Validation Solves</b></span>

Cross validation addresses **three core problems**.

---

### Problem 1 — High Variance Evaluation

Single split evaluation depends heavily on random sampling.

Cross validation reduces variance by averaging across folds.

---

### Problem 2 — Efficient Data Usage

In a simple train-test split:

```
20% data used only for testing
```

Cross validation allows **every data point to be used for both training and testing**.

Example with 5-fold:

```
Each sample:
trained on 4 times
tested once
```

---

### Problem 3 — Model Selection Bias

When comparing models:

```
Model A
Model B
Model C
```

A single test split may favor one model randomly.

Cross validation provides a **more stable comparison**.

---

# <span style="color:#2E86C1"><b>7. Cross Validation and Overfitting</b></span>

Overfitting occurs when a model memorizes training data.

Example:

```
Train R² = 0.99
Test R² = 0.72
```

Cross validation reveals this pattern clearly.

Example CV results:

```
Fold1 → 0.74
Fold2 → 0.71
Fold3 → 0.69
Fold4 → 0.72
Fold5 → 0.70
```

This shows poor generalization.

---

# <span style="color:#2E86C1"><b>8. Cross Validation in Model Development</b></span>

Typical ML workflow:

```
Dataset
↓
Feature engineering
↓
Cross validation
↓
Model comparison
↓
Hyperparameter tuning
↓
Final model selection
```

Tools like **scikit-learn** implement cross validation using functions such as:

- KFold
- cross_val_score

---

# <span style="color:#2E86C1"><b>9. Intuition</b></span>

Imagine you want to estimate how good a chef is.

One meal evaluation is unreliable.

Instead:

```
Taste multiple meals
Average the ratings
```

Cross validation does the same thing for models.

---

# <span style="color:#2E86C1"><b>Key Insight</b></span>

Cross validation exists because:

```
We cannot observe future data.
```

So we **simulate multiple future scenarios using the existing dataset** and average the outcomes.

This provides a **lower-variance and more reliable estimate of real-world model performance**.
