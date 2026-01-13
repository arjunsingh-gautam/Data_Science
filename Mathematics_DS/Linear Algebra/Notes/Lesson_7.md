<span style="color:orange; font-size:26px; font-weight:bold;">Use of Linear Dependence in Machine Learning — Explained from First Principles</span>

**Navigation**

1. <a href="#fp"><span style="color:red;">First-principle intuition (why ML even cares)</span></a>
2. <a href="#features"><span style="color:red;">Feature redundancy & multicollinearity</span></a>
3. <a href="#rank"><span style="color:red;">Rank, information content & identifiability</span></a>
4. <a href="#optimization"><span style="color:red;">Optimization, instability & overfitting</span></a>
5. <a href="#dim"><span style="color:red;">Dimensionality reduction (PCA, SVD)</span></a>
6. <a href="#regularization"><span style="color:red;">Regularization uses dependence intentionally</span></a>
7. <a href="#nn"><span style="color:red;">Neural networks & learned dependence</span></a>
8. <a href="#example"><span style="color:red;">Concrete numeric example</span></a>

---

<span id="fp" style="color:red; font-size:20px; font-weight:bold;">1. First-principle intuition (why ML even cares)</span>

From first principles, **machine learning tries to learn a mapping from inputs → outputs using information present in data**.

If two input vectors (features) are **linearly dependent**, then:

- They carry **overlapping information**
- One does **not add a new direction** in feature space

So ML asks a basic question:

> _How many truly independent directions of information exist in my data?_

Linear dependence answers this.

---

<span id="features" style="color:red; font-size:20px; font-weight:bold;">2. Feature redundancy & multicollinearity</span>

Suppose features are:

x₃ = 2x₁ + x₂

From first principles:

- x₃ adds **no new information**
- The model sees the **same signal repeated**

This situation is called **multicollinearity**.

Why it matters:

- Coefficients become **unstable**
- Model explanations become unreliable
- Training can be numerically fragile

So:

> **Linear dependence tells us which features are redundant.**

---

<span id="rank" style="color:red; font-size:20px; font-weight:bold;">3. Rank, information content & identifiability</span>

Data in ML is stored as a matrix **X** (samples × features).

From linear algebra:

- **Rank(X)** = number of linearly independent columns
- Rank = **effective information dimension**

If columns are linearly dependent:

- Rank < number of features
- Multiple parameter vectors give the **same predictions**

So:

> **Linear dependence ⇒ parameters are not uniquely identifiable**

This is critical in:

- Linear regression
- Logistic regression
- Econometric models

---

<span id="optimization" style="color:red; font-size:20px; font-weight:bold;">4. Optimization, instability & overfitting</span>

From first principles of optimization:

Learning means minimizing a loss surface.

With linearly dependent features:

- Loss surface becomes **flat in some directions**
- Gradients don’t give a unique direction
- Small noise → large coefficient changes

Result:

- Slow or unstable convergence
- Overfitting without real performance gain

Thus:

> **Linear dependence creates ill-conditioned optimization problems.**

---

<span id="dim" style="color:red; font-size:20px; font-weight:bold;">5. Dimensionality reduction (PCA, SVD)</span>

PCA starts from a first-principle question:

> _Which directions in data actually vary?_

Steps:

- Find directions with **maximum variance**
- Discard directions with **zero or near-zero variance**

Those discarded directions correspond to:

- Exact or approximate **linear dependence**

So PCA:

> **Removes linearly dependent (or nearly dependent) directions automatically**

This improves:

- Speed
- Generalization
- Interpretability

---

<span id="regularization" style="color:red; font-size:20px; font-weight:bold;">6. Regularization uses dependence intentionally</span>

Regularization changes the learning objective.

### L2 (Ridge)

- Distributes weight across correlated (dependent) features
- Stabilizes solutions

### L1 (Lasso)

- Forces some coefficients to **zero**
- Selects one feature among dependent ones

From first principles:

> **Regularization manages linear dependence instead of ignoring it.**

---

<span id="nn" style="color:red; font-size:20px; font-weight:bold;">7. Neural networks & learned dependence</span>

Neural networks **learn representations**.

Hidden layers often:

- Combine features linearly
- Create new dependent/independent directions

Early layers:

- Remove redundancy
- Compress dependent features

So:

> **Neural networks internally learn and reshape linear dependence.**

---

<span id="example" style="color:red; font-size:20px; font-weight:bold;">8. Concrete numeric example</span>

Features:

- x₁ = house size (sqft)
- x₂ = number of rooms
- x₃ = 0.5 × house size

Here:
x₃ = 0.5x₁ → linearly dependent

Effects:

- Regression coefficients become unstable
- Removing x₃ does **not reduce accuracy**
- PCA will drop x₃ direction automatically

This shows:

> **Dependence = redundancy, not power**

---

### One-line first-principle takeaway

> **In machine learning, linear dependence tells us how many truly independent directions of information exist in data—and learning quality depends on using those directions, not redundant ones.**

---
