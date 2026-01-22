<span style="color:#bc7930; font-size:26px; font-weight:bold;">Why Matrix–Vector Multiplication Is a Linear Combination of Column Vectors (First-Principles Explanation)</span>

**Navigation**

1. <a href="#property"><span style="color:red;">What exactly happens when a matrix multiplies a vector</span></a>
2. <a href="#proof"><span style="color:red;">First-principle derivation (mathematical proof)</span></a>
3. <a href="#meaning"><span style="color:red;">Geometric & structural meaning of the property</span></a>
4. <a href="#useful"><span style="color:red;">Why this property is fundamentally useful</span></a>
5. <a href="#ml"><span style="color:red;">Uses of this property in ML / AI (with examples)</span></a>
6. <a href="#extra"><span style="color:red;">Important insights most people miss</span></a>

---

<span id="property" style="color:red; font-size:20px; font-weight:bold;">1. What exactly happens when a matrix multiplies a vector</span>

Let a matrix (A) have columns (c_1, c_2, \dots, c_n):

[
A = [, c_1 ; c_2 ; \dots ; c_n ,]
]

Let a vector be:

[
x = \begin{bmatrix}
x_1 \ x_2 \ \vdots \ x_n
\end{bmatrix}
]

Then **matrix–vector multiplication means**:

[
Ax = x_1 c_1 + x_2 c_2 + \dots + x_n c_n
]

👉 **Result**:

> Multiplying a matrix by a vector is the **linear combination of the matrix’s column vectors**, where the vector entries are the **scaling coefficients**.

This is not an interpretation — it is the **definition unfolding itself**.

---

<span id="proof" style="color:red; font-size:20px; font-weight:bold;">2. First-principle derivation (why this is true)</span>

Start from the basic definition of matrix multiplication.

Let:

[
A =
\begin{bmatrix}
a_{11} & a_{12} & \dots & a_{1n} \
a_{21} & a_{22} & \dots & a_{2n} \
\vdots & \vdots & & \vdots \
a_{m1} & a_{m2} & \dots & a_{mn}
\end{bmatrix},
\quad
x =
\begin{bmatrix}
x_1 \ x_2 \ \vdots \ x_n
\end{bmatrix}
]

Then the product (Ax) is:

[
Ax =
\begin{bmatrix}
a_{11}x_1 + a_{12}x_2 + \dots + a_{1n}x_n \
a_{21}x_1 + a_{22}x_2 + \dots + a_{2n}x_n \
\vdots \
a_{m1}x_1 + a_{m2}x_2 + \dots + a_{mn}x_n
\end{bmatrix}
]

Now regroup by coefficients:

[
Ax =
x*1
\begin{bmatrix}
a*{11} \ a*{21} \ \vdots \ a*{m1}
\end{bmatrix}

- x*2
  \begin{bmatrix}
  a*{12} \ a*{22} \ \vdots \ a*{m2}
  \end{bmatrix}

* \dots +
  x*n
  \begin{bmatrix}
  a*{1n} \ a*{2n} \ \vdots \ a*{mn}
  \end{bmatrix}
  ]

Each bracket is a **column vector of A**.

So mathematically:

[
Ax = \sum_{i=1}^n x_i c_i
]

✔ Proven from first principles.

---

<span id="meaning" style="color:red; font-size:20px; font-weight:bold;">3. Geometric & structural meaning</span>

From a **geometric viewpoint**:

- Columns of (A) are **basis-like directions**
- The vector (x) gives **how much to move** along each direction
- The result is the **final position**

So:

> A matrix defines a **space of reachable outputs** (its column space),
> and vector multiplication chooses a **point inside that space**.

This directly links to:

- span
- linear independence
- dimension
- rank

---

<span id="useful" style="color:red; font-size:20px; font-weight:bold;">4. Why this property is fundamentally useful</span>

### 🔹 1. It explains what a matrix really _is_

A matrix is **not just numbers**.

> A matrix is a **collection of vectors**, and multiplication is **mixing them**.

---

### 🔹 2. It tells what outputs are possible

Because:
[
Ax \in \text{span of columns of } A
]

So:

- If a vector is **outside the column space**, no input (x) can produce it
- This explains **solvability of linear systems**

---

### 🔹 3. It explains rank & redundancy

If some columns are linearly dependent:

- Their contributions overlap
- Matrix has **fewer degrees of freedom**

This directly affects:

- stability
- identifiability
- expressiveness

---

### 🔹 4. It explains change of basis

Choosing different columns = choosing different **coordinate directions**.

---

<span id="ml" style="color:red; font-size:20px; font-weight:bold;">5. Use of this property in ML / AI (with examples)</span>

### 🔹 Example 1: Linear regression

[
\hat{y} = Xw
]

Interpretation using the property:

- Columns of (X) = feature vectors
- (w_i) = importance (weight) of each feature
- Prediction = **weighted sum of feature columns**

So:

> Model output lies in the **span of feature vectors**

If target lies outside → perfect prediction impossible.

---

### 🔹 Example 2: Neural network layer

[
z = Wx
]

Means:
[
z = x_1 c_1 + x_2 c_2 + \dots
]

Each neuron computes:

- a **linear mixture** of learned column vectors

Learning = learning **better column directions**.

---

### 🔹 Example 3: Embeddings (NLP / Vision)

Embedding matrix:

- Columns represent **latent semantic directions**
- Input vector selects and mixes them

So meaning = **linear combination of concepts**.

---

### 🔹 Example 4: PCA

Projection:
[
z = U^T x
]

Means:

- expressing data as combination of **principal directions**
- removing weak columns = dimensionality reduction

---

<span id="extra" style="color:red; font-size:20px; font-weight:bold;">6. Important insights most people miss</span>

### 🔹 Row vs column interpretation

- (Ax): column combination
- (x^TA): row combination
  Different viewpoints, same algebra.

---

### 🔹 Why bias breaks subspace structure

Bias adds a **shift**, not a combination of columns → affine space.

---

### 🔹 Rank = expressive power

Rank tells how many **independent column directions** exist → capacity.

---

### 🔹 Why overparameterization still works

Many columns but low effective rank → redundancy + regularization.

---

## ✅ Final first-principle takeaway

> **Matrix–vector multiplication is not a black-box operation: it is the act of constructing an output by linearly combining the matrix’s column vectors, with the vector entries acting as scaling coefficients. This idea underpins span, rank, expressiveness, and learning in ML/AI.**
