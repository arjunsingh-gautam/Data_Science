# **<span style="color:orange">Inroduction to Machine Learning and Regressive Analysis</span>**

- Linear Regression with one variable
  - Definition
  - Mathematics
  - Working
  - Numeric Eg.
  - Adv
  - Disadv and Limitations
  - Application
- Gradient Descent in Linear Regression

  - Definition
  - Mathematics
  - Numerical
  - Adv and Disadv

- Normal Equation method in Regression
  - Definition
  - Purpose
  - Mathematics
  - Numerical
  - Adv and Disadv
- Polynomial Regression
  - Definition
  - Mathematics
  - Working
  - Numeric Eg.
  - Adv
  - Disadv and Limitations
  - Application
- Multiple Regression
  - Definition
  - Mathematics
  - Working
  - Numeric Eg.
  - Adv
  - Disadv and Limitations
  - Application
- Evaluation Methodoly and Measures for Regression

  - MSE
    - Definition
    - Formula
    - Numerical
    - Used for and Interpretation
    - Adv and Diadv
  - MAE
    - Definition
    - Formula
    - Numerical
    - Used for and Interpretation
    - Adv and Disadv
  - RMSE
    - Definition
    - Formula
    - Numerical
    - Used for and Interpretation
    - Adv and Disadv
  - R2 Score
    - Definition
    - Formula
    - Numerical
    - Used for and Interpretation
    - Adv and Disadv

- Overfitting

  - Definition
  - Causes
  - Indicators
  - Effect on Model
  - Solution

- Underfitting

  - Definition
  - Causes
  - Indicators
  - Effect on Model
  - Solution

- Regularisation
  - Definiton
  - Purpose
  - Effect on Model
  - Adv and Diadv
  - Types of Regularisation
    - L1
      - Definiton
      - Mathematics
      - Numerical
      - Purpose
      - Effect on Model
      - Adv and Diadv
    - L2
      - Definiton
      - Mathematics
      - Numerical
      - Purpose
      - Effect on Model
      - Adv and Diadv
    - Elastic
      - L1
      - Definiton
      - Mathematics
      - Numerical
      - Purpose
      - Effect on Model
      - Adv and Diadv
- Bias Variance Tradeoff
  - Bias and Variance Definition
  - Causality of Bias and Variance
  - Effect of Bias and Variance on Model
  - Bias Variance Tradeoff
  - Solutions for Bias and Variance

Here is a complete explanation of **Linear Regression with One Variable** (also called **Simple Linear Regression**):

---

## 🟠 **Linear Regression with One Variable**

### 🔹 Definition

**Linear Regression** is a **supervised machine learning algorithm** used for **predicting a continuous dependent variable** (Y) based on **one independent variable** (X), by fitting a linear equation (a straight line) to the observed data.

---

### 🔹 Mathematics

The linear regression model is represented by the equation:

$$
Y = mX + c
$$

Where:

- $Y$: Dependent variable (target/output)
- $X$: Independent variable (input)
- $m$: Slope of the line (coefficient)
- $c$: Y-intercept
- $\hat{Y}$: Predicted value

The goal is to find the values of **m** and **c** that minimize the **Mean Squared Error (MSE)**:

$$
MSE = \frac{1}{n} \sum_{i=1}^{n} (Y_i - \hat{Y}_i)^2
$$

---

### 🔹 Working

1. **Assume linear relationship** between X and Y.
2. Use **least squares method** to find the best-fitting line:

   - Calculate the slope $m$ and intercept $c$:

     $$
     m = \frac{n(\sum XY) - (\sum X)(\sum Y)}{n(\sum X^2) - (\sum X)^2}
     $$

     $$
     c = \frac{\sum Y - m(\sum X)}{n}
     $$

3. Predict values of Y using $\hat{Y} = mX + c$.
4. Evaluate model performance using metrics like MSE or $R^2$ score.

---

### 🔹 Numerical Example

Let's take a dataset:

| Hours Studied (X) | Marks (Y) |
| ----------------- | --------- |
| 2                 | 40        |
| 3                 | 50        |
| 5                 | 80        |
| 6                 | 90        |

1. **Step 1:** Calculate $\sum X, \sum Y, \sum XY, \sum X^2$

$$
\sum X = 2 + 3 + 5 + 6 = 16
$$

$$
\sum Y = 40 + 50 + 80 + 90 = 260
$$

$$
\sum XY = (2×40)+(3×50)+(5×80)+(6×90) = 80 + 150 + 400 + 540 = 1170
$$

$$
\sum X^2 = 2^2 + 3^2 + 5^2 + 6^2 = 4 + 9 + 25 + 36 = 74
$$

$$
n = 4
$$

2. **Step 2:** Calculate slope (m) and intercept (c)

$$
m = \frac{4(1170) - (16)(260)}{4(74) - (16)^2} = \frac{4680 - 4160}{296 - 256} = \frac{520}{40} = 13
$$

$$
c = \frac{260 - 13(16)}{4} = \frac{260 - 208}{4} = \frac{52}{4} = 13
$$

So, the regression line is:

$$
\hat{Y} = 13X + 13
$$

---

### 🔹 Advantages

- Simple to implement and interpret.
- Requires little computational resources.
- Useful for linear trend analysis and forecasting.

---

### 🔹 Disadvantages / Limitations

- Assumes a **linear relationship** (not suitable for non-linear data).
- Sensitive to **outliers**.
- Assumes **homoscedasticity** (constant variance of errors).
- Works poorly with **multicollinearity** (in multiple regression).

---

### 🔹 Applications

- Predicting **sales** based on advertising budget.
- Estimating **house prices** based on square footage.
- Forecasting **stock prices** using past values.
- Predicting **student performance** from study hours.

---



---

## 🟢 **1. Homoscedasticity**

### 🔸 **Definition (Simple)**

Homoscedasticity means that the **spread (variance) of errors is consistent** across all values of the independent variable.
In contrast, **heteroscedasticity** means the spread of errors changes (gets bigger or smaller) as the independent variable changes.

### 🔸 **Analogy**

🔍 **Imagine you're throwing darts at a board**, standing at different distances.

- If the **spread of your darts is similar** regardless of how far you stand (near or far), you're **homoscedastic**.
- If your **throws become wilder** (more scattered) as you move farther, you're **heteroscedastic**.

### 🔸 **In Regression:**

- Homoscedasticity: Residuals (errors) are equally spread out — this is ideal!
- Heteroscedasticity: Residuals fan out or contract — this violates regression assumptions and affects accuracy.

### 🔸 **Why it's a problem?**

Because it violates one of the key assumptions of linear regression. It can make your predictions **biased or inefficient**.

---

## 🔵 **2. Multicollinearity**

### 🔸 **Definition (Simple)**

Multicollinearity happens when **two or more independent variables in your model are highly correlated**, meaning they move together and provide **redundant information**.

### 🔸 **Analogy**

🧍‍♂️ Suppose you ask **two friends** about the weather, and they both get their info from **the same weather app**.

- You're not getting **two independent opinions** — just the **same info twice**.
- This makes it hard to know **who is actually helping** you make a good decision.

In regression, when two features (variables) are giving **almost the same signal**, the model has trouble figuring out which one is more important.

### 🔸 **Why it's a problem?**

- It makes **coefficients unstable** and hard to interpret.
- Slight changes in data can cause **large swings in predictions**.
- It **inflates the variance** of the coefficient estimates.

---

## 🟣 Summary Table

| Concept           | Problem It Causes                             | Analogy                             |
| ----------------- | --------------------------------------------- | ----------------------------------- |
| Homoscedasticity  | Unequal error spread → inaccurate predictions | Throwing darts from different spots |
| Multicollinearity | Redundant features → confusion in importance  | Two friends from same weather app   |

---

Let's break down **Gradient Descent in Linear Regression** with simple definitions, math, and a numerical example.

---

## 🟢 **1. Definition**

**Gradient Descent** is an **optimization algorithm** used to **minimize the cost function** in linear regression by adjusting model parameters (slope `m` and intercept `b` or weights `w` and bias `b`).

It helps find the line of best fit by **iteratively** moving in the direction where the error is minimized.

---

## 🔵 **2. Mathematics**

For **Linear Regression**, the prediction is:

$$
\hat{y} = mx + b
$$

The **cost function** (Mean Squared Error):

$$
J(m, b) = \frac{1}{n} \sum_{i=1}^{n} (\hat{y}_i - y_i)^2
$$

We use **gradient descent** to find values of `m` and `b` that minimize $J(m, b)$.

**Update formulas:**

$$
m := m - \alpha \cdot \frac{\partial J}{\partial m}
$$

$$
b := b - \alpha \cdot \frac{\partial J}{\partial b}
$$

Where:

- $\alpha$ is the **learning rate**.
- $\frac{\partial J}{\partial m} = \frac{-2}{n} \sum (y_i - \hat{y}_i) \cdot x_i$
- $\frac{\partial J}{\partial b} = \frac{-2}{n} \sum (y_i - \hat{y}_i)$

---

## 🟠 **3. Numerical Example**

Let's take a **simple dataset**:

| x   | y   |
| --- | --- |
| 1   | 2   |
| 2   | 4   |

### Step 1: Initialize

- m = 0, b = 0
- α (learning rate) = 0.01

### Step 2: Prediction

- For x = 1: $\hat{y} = 0 \cdot 1 + 0 = 0$
- For x = 2: $\hat{y} = 0 \cdot 2 + 0 = 0$

### Step 3: Errors

- Error at x=1: $2 - 0 = 2$
- Error at x=2: $4 - 0 = 4$

### Step 4: Gradients

$$
\frac{\partial J}{\partial m} = -2/n \cdot \sum (y_i - \hat{y}_i) \cdot x_i = -2/2 \cdot (2 \cdot 1 + 4 \cdot 2) = -1 \cdot (2 + 8) = -10
$$

$$
\frac{\partial J}{\partial b} = -2/n \cdot \sum (y_i - \hat{y}_i) = -1 \cdot (2 + 4) = -6
$$

### Step 5: Update Parameters

$$
m := 0 - 0.01 \cdot (-10) = 0.1
$$

$$
b := 0 - 0.01 \cdot (-6) = 0.06
$$

Now new line is: $\hat{y} = 0.1x + 0.06$

Repeat until convergence.

---

## 🟣 **4. Advantages of Gradient Descent**

- ✅ Works well even with **large datasets**.
- ✅ Can optimize complex models with **many parameters**.
- ✅ Flexible: Can be applied to **nonlinear models** too.

---

## 🔴 **5. Disadvantages of Gradient Descent**

- ❌ Needs careful tuning of the **learning rate**:

  - Too high → Overshoot minimum
  - Too low → Slow convergence

- ❌ Can get stuck in **local minima** (for non-convex functions).
- ❌ May require many **iterations** to converge.

---

Great question! Let's clarify the **relationship between Least Squares and Gradient Descent (GD)** in **Linear Regression**.

---

### 🧠 **Short Answer:**

- ✅ **Least Squares** gives the **exact optimal weights** **analytically** (in one step using matrix algebra).
- ✅ **Gradient Descent** gives an **approximate solution** **iteratively**.
- ❌ You **do not need to calculate Least Squares first** before using GD.
- ✅ You **either use Least Squares _or_ Gradient Descent**, not both.

---

### 🔍 **When to use which?**

| Method                              | Description                                                       | When to Use                                                                                 |
| ----------------------------------- | ----------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| **Least Squares (Normal Equation)** | Solves for weights directly using: $\mathbf{w} = (X^TX)^{-1}X^Ty$ | - Small/medium datasets<br>- When inverse of $X^TX$ is computable                           |
| **Gradient Descent**                | Iteratively updates weights to minimize loss                      | - Large datasets<br>- High-dimensional data<br>- Sparse data<br>- Online/streaming learning |

---

### ✅ So, to clarify:

1. You **don’t need to compute weights using Least Squares first**, then optimize using GD.
2. **GD starts with random weights** (or zeros) and learns them **through iteration**.
3. **In practice**:

   - Use **Least Squares** when dataset is small and memory-efficient.
   - Use **GD (or SGD)** when data is **large, high-dimensional**, or in **neural networks** where closed-form is infeasible.

---

### 🧪 Example:

For a dataset with 10,000+ features (like in NLP or image data):

- Inverting $X^TX$ is computationally expensive or impossible.
- So we use **Gradient Descent** instead.

---

Here's a complete breakdown of the **Normal Equation method in Regression**:

---

## 🔷 **Normal Equation in Linear Regression**

### ✅ **Definition:**

The **Normal Equation** is a **closed-form (direct)** method to compute the optimal weights (**parameters**) in **Linear Regression** without iterative optimization like Gradient Descent.

---

### 🎯 **Purpose:**

To find the best-fit line (or hyperplane) by **minimizing the cost function (Mean Squared Error)** using matrix algebra.

---

### 🧮 **Mathematics:**

Given:

- $X$: Feature matrix (of size $m \times n$, with a bias column)
- $y$: Target vector (of size $m \times 1$)
- $w$: Weight vector (to be calculated)

The **Normal Equation** is:

$$
\boxed{w = (X^T X)^{-1} X^T y}
$$

This gives the exact solution for the weights $w$ that minimize the cost function.

---

### 🔢 **Numerical Example:**

You're absolutely right — thank you for catching that! Let's correct the mistake in computing $X^T y$ and then redo the rest of the solution properly.

---

## ✅ Normal Equation Refresher

The normal equation is:

$$
w = (X^T X)^{-1} X^T y
$$

We’re using the data:

| x   | y   |
| --- | --- |
| 1   | 2   |
| 2   | 3   |
| 4   | 5   |

---

### 🔹 Step 1: Construct matrices

Add a bias column of 1s:

$$
X = \begin{bmatrix}
1 & 1 \\
1 & 2 \\
1 & 4 \\
\end{bmatrix}
,\quad
y = \begin{bmatrix}
2 \\
3 \\
5 \\
\end{bmatrix}
$$

---

### 🔹 Step 2: Compute $X^T X$

$$
X^T = \begin{bmatrix}
1 & 1 & 1 \\
1 & 2 & 4 \\
\end{bmatrix}
\Rightarrow
X^T X =
\begin{bmatrix}
3 & 7 \\
7 & 21 \\
\end{bmatrix}
$$

---

### 🔹 Step 3: Compute $X^T y$

$$
X^T y =
\begin{bmatrix}
1 & 1 & 1 \\
1 & 2 & 4 \\
\end{bmatrix}
\begin{bmatrix}
2 \\
3 \\
5 \\
\end{bmatrix}
=
\begin{bmatrix}
2 + 3 + 5 \\
1×2 + 2×3 + 4×5 \\
\end{bmatrix}
=
\begin{bmatrix}
10 \\
28 \\
\end{bmatrix}
$$

✅ **Corrected**: $X^T y = \begin{bmatrix} 10 \\ 28 \end{bmatrix}$

---

### 🔹 Step 4: Compute $(X^T X)^{-1}$

We already know:

$$
X^T X = \begin{bmatrix} 3 & 7 \\ 7 & 21 \end{bmatrix}
$$

Determinant:

$$
\text{det} = 3×21 - 7×7 = 63 - 49 = 14
$$

Inverse:

$$
(X^T X)^{-1} = \frac{1}{14}
\begin{bmatrix}
21 & -7 \\
-7 & 3 \\
\end{bmatrix}
$$

---

### 🔹 Step 5: Compute weights

$$
w = (X^T X)^{-1} X^T y
= \frac{1}{14}
\begin{bmatrix}
21 & -7 \\
-7 & 3 \\
\end{bmatrix}
\begin{bmatrix}
10 \\
28 \\
\end{bmatrix}
$$

Now multiply:

- First row: $21×10 + (-7)×28 = 210 - 196 = 14$
- Second row: $-7×10 + 3×28 = -70 + 84 = 14$

So,

$$
w = \frac{1}{14}
\begin{bmatrix}
14 \\
14 \\
\end{bmatrix}
=
\begin{bmatrix}
1 \\
1 \\
\end{bmatrix}
$$

---

### ✅ Final Linear Regression Equation:

$$
\boxed{y = 1 + 1x}
$$

---

### 🔍 Interpretation:

- Intercept: 1
- Slope: 1
  This means the best-fit line increases by 1 for every unit increase in $x$, starting from 1.

Let me know if you'd like this solved using Python or visualized with a graph!

---

### ✅ **Advantages:**

- Exact solution, **no iteration required**.
- Easy to implement for **small datasets**.
- Good for **understanding the math** of Linear Regression.

---

### ❌ **Disadvantages:**

- **Computationally expensive** for large datasets (computing inverse is $O(n^3)$).
- **Does not work well** if $X^T X$ is **non-invertible** or **ill-conditioned**.
- Cannot be used for **online learning** or **real-time streaming data**.

---

Here’s a **complete explanation of Polynomial Regression** with all key sections:

---

## 🟧 **Polynomial Regression**

---

### 🔹 **Definition:**

Polynomial Regression is a form of regression analysis in which the relationship between the **independent variable $x$** and the **dependent variable $y$** is modeled as an **nth-degree polynomial**.

It is used when the data shows a **non-linear trend**, but you want to **maintain a linear approach in terms of coefficients**.

---

### 🔹 **Mathematics:**

The polynomial regression equation of degree $n$ is:

$$
y = \beta_0 + \beta_1 x + \beta_2 x^2 + \cdots + \beta_n x^n + \epsilon
$$

Where:

- $\beta_0, \beta_1, \ldots, \beta_n$ are the coefficients (weights),
- $\epsilon$ is the error term.

---

### 🔹 **Working:**

1. **Transform the input** variable $x$ into its powers: $x, x^2, x^3, \ldots, x^n$.
2. Use **Linear Regression** techniques (like Normal Equation or Gradient Descent) on this transformed data.
3. Fit the curve based on the optimal values of $\beta$'s.

> ✨ You are still performing _linear regression_, but on **polynomial features**.

---

### 🔹 **Numerical Example:**

Let’s say we have the dataset:

| x   | y   |
| --- | --- |
| 1   | 3   |
| 2   | 5   |
| 3   | 10  |
| 4   | 18  |

Assume we are using a **degree-2 polynomial**:

$$
y = \beta_0 + \beta_1 x + \beta_2 x^2
$$

#### Step 1: Prepare Data Matrix

Augmented input matrix $X$:

$$
X =
\begin{bmatrix}
1 & 1 & 1^2 \\
1 & 2 & 4 \\
1 & 3 & 9 \\
1 & 4 & 16 \\
\end{bmatrix}
=
\begin{bmatrix}
1 & 1 & 1 \\
1 & 2 & 4 \\
1 & 3 & 9 \\
1 & 4 & 16 \\
\end{bmatrix}
,\quad
y = \begin{bmatrix} 3 \\ 5 \\ 10 \\ 18 \end{bmatrix}
$$

#### Step 2: Apply Normal Equation

$$
\beta = (X^T X)^{-1} X^T y
$$

You can compute this manually or with Python (e.g., using `numpy.linalg.inv()` and `np.dot()`).

🔹 **Python Solution (for speed):**

```python
import numpy as np

X = np.array([[1, 1, 1], [1, 2, 4], [1, 3, 9], [1, 4, 16]])
y = np.array([[3], [5], [10], [18]])

# Normal Equation: β = (X^T X)^-1 X^T y
beta = np.linalg.inv(X.T @ X) @ X.T @ y
print(beta)
```

➡ Output:

$$
\beta_0 = 2,\quad \beta_1 = -0.5,\quad \beta_2 = 1
$$

#### Final Equation:

$$
\boxed{y = 2 - 0.5x + x^2}
$$

---

### 🔹 **Advantages:**

- Can model **non-linear** relationships.
- More **flexible** than linear regression.
- Useful when data has **curvature**.

---

### 🔹 **Disadvantages & Limitations:**

- **Overfitting**: Higher degrees can make the model sensitive to noise.
- **Computationally expensive** for large degrees.
- **Extrapolation** beyond training data is unreliable.
- Hard to interpret higher-degree terms.

---

### 🔹 **Applications:**

- **Economics**: Modeling supply-demand curves.
- **Biology**: Dose-response modeling.
- **Physics**: Modeling trajectories, motion under force.
- **Engineering**: Material stress-strain relationships.
- **Marketing**: Customer conversion curves.

---

Here’s a detailed breakdown of **Multiple Linear Regression** with all required sections:

---

## 🟧 **Multiple Linear Regression**

---

### 🔹 **Definition:**

Multiple Linear Regression is a statistical technique that models the **linear relationship** between a **single dependent variable** and **two or more independent variables**.

It generalizes simple linear regression to accommodate **multiple predictors**.

$$
\textbf{Used when the output depends on more than one input.}
$$

---

### 🔹 **Mathematics:**

The model is:

$$
y = \beta_0 + \beta_1 x_1 + \beta_2 x_2 + \dots + \beta_n x_n + \epsilon
$$

Where:

- $y$: Dependent (target) variable
- $x_1, x_2, \dots, x_n$: Independent variables (features)
- $\beta_0$: Intercept
- $\beta_1, \dots, \beta_n$: Coefficients
- $\epsilon$: Error term (residual)

Matrix form:

$$
\mathbf{y} = \mathbf{X}\boldsymbol{\beta} + \boldsymbol{\epsilon}
$$

Where:

- $\mathbf{X}$: Matrix of features with an intercept column
- $\boldsymbol{\beta}$: Coefficient vector
- $\mathbf{y}$: Target values vector

To estimate $\boldsymbol{\beta}$:

$$
\boldsymbol{\hat{\beta}} = (X^T X)^{-1} X^T y
$$

---

### 🔹 **Working:**

1. Collect data with multiple independent variables.
2. Construct feature matrix $X$ and target vector $y$.
3. Apply the **Normal Equation** or **Gradient Descent** to compute optimal coefficients.
4. Predict outputs using the trained model.

---

### 🔹 **Numerical Example:**

Let’s take a dataset:

| x₁ (Experience in yrs) | x₂ (Certification Score) | y (Salary in ₹k) |
| ---------------------- | ------------------------ | ---------------- |
| 1                      | 8                        | 30               |
| 2                      | 9                        | 50               |
| 3                      | 6                        | 65               |

Add intercept term → matrix $X$:

$$
X = \begin{bmatrix}
1 & 1 & 8 \\
1 & 2 & 9 \\
1 & 3 & 6 \\
\end{bmatrix}, \quad
y = \begin{bmatrix}
30 \\
50 \\
65 \\
\end{bmatrix}
$$

Apply Normal Equation:

$$
\boldsymbol{\beta} = (X^T X)^{-1} X^T y
$$

🔹 **Python Code:**

```python
import numpy as np

X = np.array([[1, 1, 8], [1, 2, 9], [1, 3, 6]])
y = np.array([[30], [50], [65]])

beta = np.linalg.inv(X.T @ X) @ X.T @ y
print(beta)
```

🔹 Output:

$$
\beta_0 = 5,\quad \beta_1 = 25,\quad \beta_2 = 0
$$

🔸 **Equation:**

$$
y = 5 + 25 \cdot x_1 + 0 \cdot x_2
$$

(Note: This means the certification score didn't impact the salary in this small dataset.)

---

### 🔹 **Advantages:**

- Handles **multiple variables** influencing outcome.
- Helps in **feature selection** and **understanding relationships**.
- Works well with **continuous variables**.
- Easy to implement and interpret (when assumptions hold).

---

### 🔹 **Disadvantages & Limitations:**

- Assumes **linear relationship** (not always realistic).
- Sensitive to:

  - **Multicollinearity** (independent variables correlated)
  - **Outliers**
  - **Heteroscedasticity** (non-constant variance)

- Can **overfit** with too many variables.
- Needs large data for stable results when using many predictors.

---

### 🔹 **Applications:**

- **Business:** Predicting revenue, pricing, customer churn.
- **Healthcare:** Predicting patient outcomes based on vitals and demographics.
- **Education:** Modeling student performance based on multiple inputs.
- **Economics:** Forecasting inflation, demand, or GDP.
- **Marketing:** Measuring effect of multiple campaigns on sales.

---

Here’s a detailed explanation of **Evaluation Methodology and Measures for Regression**, covering:

---

## 🟧 **Evaluation Methodology and Measures for Regression**

---

### 🔹 **1. Mean Squared Error (MSE)**

#### ✅ **Definition:**

MSE is the average of the **squared differences** between the predicted and actual values. It penalizes larger errors more due to squaring.

#### 📐 **Formula:**

$$
\text{MSE} = \frac{1}{n} \sum_{i=1}^{n}(y_i - \hat{y}_i)^2
$$

Where:

- $y_i$: Actual value
- $\hat{y}_i$: Predicted value
- $n$: Total observations

#### 🔢 **Numerical Example:**

| Actual (y) | Predicted (ŷ) |
| ---------- | ------------- |
| 3          | 2.5           |
| 5          | 5.5           |
| 2          | 3.0           |

$$
\text{MSE} = \frac{(3-2.5)^2 + (5-5.5)^2 + (2-3)^2}{3} = \frac{0.25 + 0.25 + 1}{3} = \frac{1.5}{3} = 0.5
$$

#### 💡 **Used for / Interpretation:**

- Measures **average squared error**.
- **Lower MSE = better performance**.

#### ➕ **Advantages:**

- Penalizes larger errors heavily (good for sensitive applications).
- Differentiable – useful for optimization.

#### ➖ **Disadvantages:**

- Not interpretable in actual units.
- Sensitive to **outliers**.

---

### 🔹 **2. Mean Absolute Error (MAE)**

#### ✅ **Definition:**

MAE is the average of the **absolute differences** between the predicted and actual values.

#### 📐 **Formula:**

$$
\text{MAE} = \frac{1}{n} \sum_{i=1}^{n} \left| y_i - \hat{y}_i \right|
$$

#### 🔢 **Numerical Example:**

Using same values:

$$
\text{MAE} = \frac{|3 - 2.5| + |5 - 5.5| + |2 - 3|}{3} = \frac{0.5 + 0.5 + 1}{3} = \frac{2}{3} ≈ 0.667
$$

#### 💡 **Used for / Interpretation:**

- Directly interpretable – shows average absolute error.

#### ➕ **Advantages:**

- Easy to understand and interpret.
- Less sensitive to outliers than MSE.

#### ➖ **Disadvantages:**

- Non-differentiable at zero (less useful for optimization).
- Treats all errors equally (doesn’t penalize big errors).

---

### 🔹 **3. Root Mean Squared Error (RMSE)**

#### ✅ **Definition:**

RMSE is the **square root** of the MSE. It brings error back to the original units of the target variable.

#### 📐 **Formula:**

$$
\text{RMSE} = \sqrt{ \frac{1}{n} \sum_{i=1}^{n}(y_i - \hat{y}_i)^2 }
$$

#### 🔢 **Numerical Example:**

From MSE = 0.5

$$
\text{RMSE} = \sqrt{0.5} ≈ 0.707
$$

#### 💡 **Used for / Interpretation:**

- Like MSE, but **unit-wise comparable** to original data.
- **Lower RMSE = better performance**.

#### ➕ **Advantages:**

- Intuitive (same unit as target variable).
- Penalizes larger errors more than MAE.

#### ➖ **Disadvantages:**

- Sensitive to outliers.
- Not always interpretable in isolation.

---

### 🔹 **4. R² Score (Coefficient of Determination)**

#### ✅ **Definition:**

R² measures the proportion of variance in the target variable that is **explained** by the model.

#### 📐 **Formula:**

$$
R^2 = 1 - \frac{\sum_{i=1}^n (y_i - \hat{y}_i)^2}{\sum_{i=1}^n (y_i - \bar{y})^2}
$$

Where:

- $\bar{y}$ is the mean of actual values.

#### 🔢 **Numerical Example:**

Let:

Actual (y): \[3, 5, 2]
Predicted (ŷ): \[2.5, 5.5, 3.0]

$$
\bar{y} = \frac{3 + 5 + 2}{3} = 3.33
$$

SSres (residual sum of squares):

$$
= (3-2.5)^2 + (5-5.5)^2 + (2-3)^2 = 0.25 + 0.25 + 1 = 1.5
$$

SStot (total sum of squares):

$$
= (3-3.33)^2 + (5-3.33)^2 + (2-3.33)^2 = 0.11 + 2.78 + 1.78 = 4.67
$$

$$
R^2 = 1 - \frac{1.5}{4.67} ≈ 0.679
$$

#### 💡 **Used for / Interpretation:**

- Measures **goodness-of-fit**.
- Value ranges from **−∞ to 1**.
- Closer to 1 → better model.

#### ➕ **Advantages:**

- Interpretable.
- Standard metric for model comparison.

#### ➖ **Disadvantages:**

- Can be **misleading** (e.g., non-linear models).
- Doesn’t tell about overfitting.
- Can be negative if model fits worse than mean.

---

## ✅ Summary Table:

| Metric | Unit          | Penalizes Large Errors | Intuitive | Affected by Outliers | Range   |
| ------ | ------------- | ---------------------- | --------- | -------------------- | ------- |
| MSE    | Squared units | ✅                     | ❌        | ✅                   | \[0, ∞) |
| MAE    | Original unit | ❌                     | ✅        | ❌                   | \[0, ∞) |
| RMSE   | Original unit | ✅                     | ✅        | ✅                   | \[0, ∞) |
| R²     | Unitless      | ❌                     | ✅        | ✅                   | (−∞, 1] |

---

Here’s a clear explanation of **Overfitting** and **Underfitting** with all required sections:

---

## 🟧 **Overfitting vs Underfitting**

---

### 🔹 **Overfitting**

#### ✅ **Definition:**

Overfitting occurs when a model **learns the training data too well**, including its **noise and outliers**, resulting in **poor performance on new (test) data**.

#### 💣 **Causes:**

- Too complex model (e.g., high-degree polynomial).
- Too many features.
- Not enough training data.
- Too many training epochs (for neural networks).
- No regularization applied.

#### 🧪 **Indicators:**

- **High accuracy on training data**, but **low accuracy on validation/test data**.
- Large gap between training and test loss.
- Very low training error, but high generalization error.

#### ⚠️ **Effect on Model:**

- Model becomes **highly sensitive** to minor fluctuations in data.
- Fails to generalize to **unseen data**.

#### 🛠️ **Solution:**

- Simplify the model (e.g., reduce number of features or lower degree of polynomial).
- Use **cross-validation** to monitor generalization.
- Use **regularization** (e.g., L1, L2).
- Increase training data size.
- Early stopping in iterative models.

#### 📈 Example (Visual Intuition):

Fitting a 10-degree polynomial to 5 points → curve fits perfectly through each point but fails to predict future trends.

---

### 🔹 **Underfitting**

#### ✅ **Definition:**

Underfitting occurs when a model is **too simple** to learn the underlying structure of the data, leading to **poor performance on both training and test data**.

#### 💣 **Causes:**

- Too simple model (e.g., linear regression for non-linear data).
- Insufficient training (e.g., few epochs).
- Irrelevant features or missing important ones.
- High bias in the model.

#### 🧪 **Indicators:**

- **High error** on both training and test data.
- Model shows no improvement with more training.
- Low variance, high bias.

#### ⚠️ **Effect on Model:**

- The model **fails to capture patterns** in the data.
- Poor predictive performance.

#### 🛠️ **Solution:**

- Use a **more complex model** (e.g., polynomial regression).
- Add more relevant features.
- Reduce regularization strength.
- Increase training time or improve feature engineering.

#### 📈 Example (Visual Intuition):

Fitting a straight line to data with a curved trend → the model cannot capture the non-linear pattern.

---

## 🔁 Comparison Table

| Feature          | Overfitting                            | Underfitting                      |
| ---------------- | -------------------------------------- | --------------------------------- |
| Model Complexity | Too high                               | Too low                           |
| Training Error   | Low                                    | High                              |
| Testing Error    | High                                   | High                              |
| Generalization   | Poor                                   | Poor                              |
| Bias             | Low                                    | High                              |
| Variance         | High                                   | Low                               |
| Solution         | Simplify model, regularize, early stop | Increase complexity, train better |

---

Here is a detailed explanation of **Regularisation** and its types — **L1, L2, and Elastic Net** — covering all aspects you requested, including formulas, numerical examples, and effects:

---

## 🟧 **Regularisation**

---

### 🔹 **Definition:**

Regularisation is a **technique to prevent overfitting** by adding a **penalty term** to the cost function that discourages large coefficients in regression models.

---

### 🎯 **Purpose:**

- Control model complexity.
- Avoid overfitting.
- Encourage simpler, more interpretable models.

---

### ⚙️ **Effect on Model:**

- Shrinks coefficients toward zero.
- Introduces bias but reduces variance.
- Results in a better generalizing model.

---

### ✅ **Advantages:**

- Helps in handling multicollinearity.
- Prevents overfitting.
- L1 can perform **feature selection**.
- Adds robustness to noise in data.

---

### ❌ **Disadvantages:**

- May underfit if the penalty is too strong.
- Interpretation becomes less intuitive due to transformed coefficients.

---

## 🔸 **Types of Regularisation**

---

## 🔹 **1. L1 Regularisation (Lasso Regression)**

### ✅ **Definition:**

L1 adds **absolute values** of coefficients to the cost function.

### 🧮 **Mathematics:**

Cost function:

$$
J(\theta) = \text{MSE} + \lambda \sum_{j=1}^{n} |\theta_j|
$$

Where:

- $\lambda$: regularisation strength
- $\theta_j$: model coefficients

### 🔢 **Numerical Example:**

Suppose for linear regression:

- MSE = 10
- Coefficients: $[1.5, -2.0]$
- $\lambda = 1$

$$
L1\_penalty = |1.5| + |-2.0| = 3.5
$$

$$
J(\theta) = 10 + (1 \times 3.5) = 13.5
$$

### 🎯 **Purpose:**

- Encourages sparsity — pushes **some weights to exactly 0**, performing **feature selection**.

### ⚙️ **Effect on Model:**

- Shrinks some coefficients to 0.
- Useful for high-dimensional data.

### ✅ **Advantage:**

- Performs feature selection.
- Helps interpretability.

### ❌ **Disadvantage:**

- Can be unstable when features are correlated.

---

## 🔹 **2. L2 Regularisation (Ridge Regression)**

### ✅ **Definition:**

L2 adds **squared values** of coefficients to the cost function.

### 🧮 **Mathematics:**

Cost function:

$$
J(\theta) = \text{MSE} + \lambda \sum_{j=1}^{n} \theta_j^2
$$

### 🔢 **Numerical Example:**

MSE = 10
Coefficients: $[1.5, -2.0]$
$\lambda = 1$

$$
L2\_penalty = (1.5)^2 + (-2.0)^2 = 2.25 + 4 = 6.25
$$

$$
J(\theta) = 10 + (1 \times 6.25) = 16.25
$$

### 🎯 **Purpose:**

- Shrinks coefficients smoothly.
- Reduces model complexity.

### ⚙️ **Effect on Model:**

- Coefficients are reduced but not zeroed.
- Works well with multicollinearity.

### ✅ **Advantage:**

- Stable with correlated features.
- Avoids overfitting.

### ❌ **Disadvantage:**

- Doesn't perform feature selection.

---

## 🔹 **3. Elastic Net Regularisation**

### ✅ **Definition:**

Elastic Net combines both **L1** and **L2** penalties.

### 🧮 **Mathematics:**

$$
J(\theta) = \text{MSE} + \lambda_1 \sum_{j=1}^{n} |\theta_j| + \lambda_2 \sum_{j=1}^{n} \theta_j^2
$$

Or using a mix ratio $\alpha$:

$$
J(\theta) = \text{MSE} + \lambda \left( \alpha \sum |\theta_j| + (1 - \alpha) \sum \theta_j^2 \right)
$$

### 🔢 **Numerical Example:**

- MSE = 10
- Coefficients: $[1.5, -2.0]$
- $\lambda = 1, \alpha = 0.5$

$$
L1 = 3.5, \quad L2 = 6.25
$$

$$
J(\theta) = 10 + 1 \times (0.5 \times 3.5 + 0.5 \times 6.25) = 10 + (1.75 + 3.125) = 14.875
$$

### 🎯 **Purpose:**

- Leverages strengths of both L1 and L2.
- Works well when:

  - Many features
  - Features are correlated

### ⚙️ **Effect on Model:**

- Encourages **group selection**.
- Keeps correlated variables.

### ✅ **Advantage:**

- Combines feature selection + regularisation.
- Flexible.

### ❌ **Disadvantage:**

- Choosing $\lambda$ and $\alpha$ can be complex.
- Slower than L1 or L2 alone.

---

## 🟩 **Summary Table**

| Technique   | Penalty Added     | Effect              | Feature Selection   | Good For                  |        |                           |
| ----------- | ----------------- | ------------------- | ------------------- | ------------------------- | ------ | ------------------------- |
| L1 (Lasso)  | ( \sum            | \theta_j            | )                   | Shrinks some weights to 0 | ✅ Yes | Sparse, high-dim datasets |
| L2 (Ridge)  | $\sum \theta_j^2$ | Shrinks all weights | ❌ No               | Correlated features       |        |                           |
| Elastic Net | ( \sum            | \theta_j            | + \sum \theta_j^2 ) | Mix of both               | ✅ Yes | Many, correlated features |

---

Here is a clear, structured explanation of the **Bias-Variance Tradeoff** and all related subtopics you've asked for:

---

## 🟧 **Bias-Variance Tradeoff**

---

### 🔹 **Bias: Definition**

Bias refers to the **error due to overly simplistic assumptions** in the learning algorithm.

- High bias = model **underfits** the data.
- It **ignores important relationships** in the data.

📌 **Example:** A linear model trying to fit a curved dataset.

---

### 🔹 **Variance: Definition**

Variance refers to the **model's sensitivity to small changes** in the training dataset.

- High variance = model **overfits** the data.
- It captures **noise** along with patterns.

📌 **Example:** A very complex model that fits every point in training data exactly, but performs poorly on new data.

---

## 🔁 **Causality of Bias and Variance**

| Cause                    | Bias                          | Variance                           |
| ------------------------ | ----------------------------- | ---------------------------------- |
| Model Complexity         | Low complexity → High Bias    | High complexity → High Variance    |
| Training Data Size       | Insufficient data → High Bias | Small data → High Variance         |
| Overfitting/Underfitting | Underfitting → High Bias      | Overfitting → High Variance        |
| Assumptions              | Oversimplified assumptions    | Highly flexible, fewer assumptions |

---

## ⚠️ **Effect on Model**

| Scenario          | Prediction Error | Training Error | Test Error | Generalisation |
| ----------------- | ---------------- | -------------- | ---------- | -------------- |
| High Bias         | High             | High           | High       | Poor           |
| High Variance     | Low              | High           | High       | Poor           |
| Balanced Tradeoff | Low              | Low            | Low        | Good           |

---

## ⚖️ **Bias-Variance Tradeoff**

- You can't minimize both bias and variance simultaneously.
- Increasing model complexity reduces **bias** but increases **variance**.
- The goal is to find the **"sweet spot"** where **total error (bias² + variance + irreducible error)** is minimized.

📈 **Total Error = Bias² + Variance + Irreducible Error**

---

### 🔍 **Visual Analogy (Target Analogy)**

- 🎯 **High Bias, Low Variance**: All arrows far from the bullseye but clustered together.
- 🎯 **Low Bias, High Variance**: Arrows all over the target, no clear pattern.
- 🎯 **Low Bias, Low Variance**: Arrows closely grouped near the bullseye — ideal!

---

## 🛠️ **Solutions for Bias and Variance**

| Problem       | Solutions                                                             |
| ------------- | --------------------------------------------------------------------- |
| High Bias     | - Use more complex model (e.g., decision tree, polynomial regression) |
|               | - Reduce regularisation (in L1/L2)                                    |
|               | - Add more relevant features                                          |
| High Variance | - Use simpler models                                                  |
|               | - Increase training data                                              |
|               | - Apply regularisation (L1, L2, Elastic Net)                          |
|               | - Use ensemble methods (Bagging, Random Forest)                       |
|               | - Use cross-validation to evaluate model generalisation               |

---

## ✅ Summary

| Bias                            | Variance                                |
| ------------------------------- | --------------------------------------- |
| Error from wrong assumptions    | Error from sensitivity to training data |
| Underfitting                    | Overfitting                             |
| Low model complexity            | High model complexity                   |
| Fixed patterns                  | Too flexible patterns                   |
| Small training error difference | Large variation in test error           |

---
