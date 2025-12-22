# <span style="color:#a4ac86">**Lesson-1 Introduction to Linear Algebra**</span>

## <span style="color:#a7c957">Table of Contents</span>

- [What is Linear Algebra?](#introduction)
- [What is a Vector?](#t2)
- [What is a Vector Space?](#t3)
- [What is a field?](#t4)
- [What is role of Linear Algebra in ML](#t5)

## <span style="color:#ff0054" id="introduction">**What is Linear Algebra?**</span>

### <span style="color:#f0c808">My Understanding</span>

- Linear Algebra is a branch of mathematics where we study about Linear equations,how to solve linear equations,solutions to linear equations,matrix,matrix operations,vectors and vector spaces etc.

### <span style="color:#f0c808">Knowledge Gaps</span>

**Linear Algebra** is a branch of mathematics that focuses on the study of **vectors**, **vector spaces**, **linear transformations**, and **systems of linear equations**. Key topics include:

- **Linear equations** and methods to solve them
- **Matrices** and **matrix operations** (such as addition, multiplication, and inversion)
- **Determinants** and their properties
- **Vectors**, vector operations, and their geometric interpretation
- **Vector spaces** and subspaces
- **Basis** and **dimension** of vector spaces
- **Linear transformations** and their matrix representations
- **Eigenvalues** and **eigenvectors**

---

## <span style="color:#ff0054" id="t2">**What is a Vector?**</span>

### 🔷 1. What is a Vector? (Mathematical Definition)

A **vector** is an **ordered list of numbers** (called components or elements), usually representing:

- A point in space,
- A direction and magnitude (in geometry/physics),
- Or a collection of features/data (in ML/data science).

---

### 📐 Formal Mathematical Definition:

A vector of dimension $n$ is an **element of** $\mathbb{R}^n$ (if working with real numbers):

$$
\vec{v} = \begin{bmatrix} v_1 \\ v_2 \\ \vdots \\ v_n \end{bmatrix}, \quad v_i \in \mathbb{R}
$$

So, $\vec{v} \in \mathbb{R}^n$

This is called a **column vector** (standard in linear algebra).

---

### 🔷 2. Representation of a Vector

### ➤ **Column Vector** (most common):

$$
\vec{v} = \begin{bmatrix} 3 \\ -2 \\ 7 \end{bmatrix} \in \mathbb{R}^3
$$

### ➤ **Row Vector** (less common in linear algebra):

$$
\vec{v} = \begin{bmatrix} 3 & -2 & 7 \end{bmatrix}
$$

### ➤ **Geometrically (2D or 3D)**:

- Represented as an **arrow** from origin to point $(v_1, v_2)$ or $(v_1, v_2, v_3)$

---

### 🔶 3. Basic Types of Vectors

| Type                        | Example / Meaning                                                                                                      |
| --------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| **Zero vector** ($\vec{0}$) | All components are zero: $\begin{bmatrix} 0 \\ 0 \\ \cdots \end{bmatrix}$                                              |
| **Unit vector**             | Length (magnitude) = 1                                                                                                 |
| **Standard basis vectors**  | e.g., $\vec{e}_1 = \begin{bmatrix} 1 \\ 0 \\ 0 \end{bmatrix}$, $\vec{e}_2 = \begin{bmatrix} 0 \\ 1 \\ 0 \end{bmatrix}$ |
| **Position vector**         | Points from origin to a location in space                                                                              |
| **Direction vector**        | Describes direction and magnitude only                                                                                 |

---

### 🔷 4. Vector Operations (Algebraic Properties)

### ➤ **Addition**:

$$
\vec{u} + \vec{v} = \begin{bmatrix} u_1 \\ u_2 \end{bmatrix} + \begin{bmatrix} v_1 \\ v_2 \end{bmatrix} = \begin{bmatrix} u_1 + v_1 \\ u_2 + v_2 \end{bmatrix}
$$

### ➤ **Scalar Multiplication**:

$$
a \cdot \vec{v} = a \cdot \begin{bmatrix} v_1 \\ v_2 \end{bmatrix} = \begin{bmatrix} a v_1 \\ a v_2 \end{bmatrix}
$$

---

### 🔷 5. Properties of Vectors

Here are the **main algebraic properties**:

### 🧮 **Addition Properties**:

1. **Commutativity**: $\vec{u} + \vec{v} = \vec{v} + \vec{u}$
2. **Associativity**: $(\vec{u} + \vec{v}) + \vec{w} = \vec{u} + (\vec{v} + \vec{w})$
3. **Additive Identity**: $\vec{v} + \vec{0} = \vec{v}$
4. **Additive Inverse**: $\vec{v} + (-\vec{v}) = \vec{0}$

### ✖️ **Scalar Multiplication Properties**:

1. **Distributivity (over vector addition)**: $a(\vec{u} + \vec{v}) = a\vec{u} + a\vec{v}$
2. **Distributivity (over scalar addition)**: $(a + b)\vec{v} = a\vec{v} + b\vec{v}$
3. **Associativity**: $a(b\vec{v}) = (ab)\vec{v}$
4. **Identity**: $1 \cdot \vec{v} = \vec{v}$

---

### 🔷 6. Magnitude (Norm) of a Vector

The **length** or **magnitude** of a vector $\vec{v} = \begin{bmatrix} v_1 \\ v_2 \\ \cdots \\ v_n \end{bmatrix}$ is:

$$
\|\vec{v}\| = \sqrt{v_1^2 + v_2^2 + \cdots + v_n^2}
$$

Example:

$$
\vec{v} = \begin{bmatrix} 3 \\ 4 \end{bmatrix}, \quad \|\vec{v}\| = \sqrt{3^2 + 4^2} = \sqrt{25} = 5
$$

---

### 🔷 7. Dot Product (Inner Product)

$$
\vec{u} \cdot \vec{v} = u_1v_1 + u_2v_2 + \cdots + u_nv_n
$$

Used for:

- Measuring **angle/similarity**
- Checking **orthogonality** (perpendicular: dot = 0)

---

### 🔷 Summary Table

| Concept         | Description                                         |
| --------------- | --------------------------------------------------- |
| **Vector**      | Ordered list of real numbers                        |
| **Dimension**   | Number of components                                |
| **Zero vector** | All components = 0                                  |
| **Norm**        | Length of vector                                    |
| **Dot product** | Scalar representing projection/similarity           |
| **Properties**  | Additive, scalar multiplication, distributive, etc. |

---

## <span style="color:#ff0054" id="t3">**What is a Vector Space**</span>

### 🔷 What is a Vector Space? (Detailed)

A **vector space** (also called a **linear space**) is a set of objects called **vectors**, along with two operations:

1. **Vector addition**
2. **Scalar multiplication**

These operations must satisfy **certain rules** (called axioms), and the scalars usually come from a **field**, like the real numbers $\mathbb{R}$ or complex numbers $\mathbb{C}$.

---

### 🔶 Formal Definition

A **vector space** $V$ over a field $F$ (like $\mathbb{R}$) is a set equipped with:

1. **Addition**: For any $\vec{u}, \vec{v} \in V$, their sum $\vec{u} + \vec{v} \in V$
2. **Scalar multiplication**: For any scalar $a \in F$ and vector $\vec{v} \in V$, $a\vec{v} \in V$

### These operations must satisfy 8 properties (axioms):

> (We’ll see examples right after!)

1. **Closure under addition**: $\vec{u} + \vec{v} \in V$
2. **Commutative addition**: $\vec{u} + \vec{v} = \vec{v} + \vec{u}$
3. **Associative addition**: $(\vec{u} + \vec{v}) + \vec{w} = \vec{u} + (\vec{v} + \vec{w})$
4. **Additive identity**: There exists a zero vector $\vec{0} \in V$ such that $\vec{v} + \vec{0} = \vec{v}$
5. **Additive inverse**: For every $\vec{v} \in V$, there exists $-\vec{v} \in V$ such that $\vec{v} + (-\vec{v}) = \vec{0}$
6. **Closure under scalar multiplication**: $a\vec{v} \in V$
7. **Distributivity of scalar multiplication over vector addition**: $a(\vec{u} + \vec{v}) = a\vec{u} + a\vec{v}$
8. **Distributivity over scalar addition**: $(a + b)\vec{v} = a\vec{v} + b\vec{v}$
9. **Associativity of scalar multiplication**: $a(b\vec{v}) = (ab)\vec{v}$
10. **Identity scalar**: $1 \cdot \vec{v} = \vec{v}$

---

### ✅ Example: $\mathbb{R}^2$ is a Vector Space

Let’s take:

$$
V = \mathbb{R}^2 = \left\{ \begin{bmatrix} x \\ y \end{bmatrix} : x, y \in \mathbb{R} \right\}
$$

So, each vector in this space looks like:

$$
\vec{v} = \begin{bmatrix} x \\ y \end{bmatrix}
$$

---

### ▶️ Operations:

- **Vector Addition**:

  $$
  \begin{bmatrix} x_1 \\ y_1 \end{bmatrix} + \begin{bmatrix} x_2 \\ y_2 \end{bmatrix} = \begin{bmatrix} x_1 + x_2 \\ y_1 + y_2 \end{bmatrix}
  $$

- **Scalar Multiplication**:

  $$
  a \cdot \begin{bmatrix} x \\ y \end{bmatrix} = \begin{bmatrix} ax \\ ay \end{bmatrix}
  $$

---

### ▶️ Check a few axioms:

1. **Closure under addition**:
   Two vectors in $\mathbb{R}^2$ added together give another $\mathbb{R}^2$ vector. ✅
   Example:

   $$
   \begin{bmatrix} 1 \\ 2 \end{bmatrix} + \begin{bmatrix} 3 \\ 4 \end{bmatrix} = \begin{bmatrix} 4 \\ 6 \end{bmatrix}
   $$

2. **Additive identity**:

   $$
   \vec{v} + \vec{0} = \begin{bmatrix} x \\ y \end{bmatrix} + \begin{bmatrix} 0 \\ 0 \end{bmatrix} = \begin{bmatrix} x \\ y \end{bmatrix}
   $$

3. **Additive inverse**:

   $$
   \vec{v} + (-\vec{v}) = \begin{bmatrix} x \\ y \end{bmatrix} + \begin{bmatrix} -x \\ -y \end{bmatrix} = \begin{bmatrix} 0 \\ 0 \end{bmatrix}
   $$

4. **Scalar multiplication**:

   $$
   2 \cdot \begin{bmatrix} 3 \\ 5 \end{bmatrix} = \begin{bmatrix} 6 \\ 10 \end{bmatrix}
   $$

All other axioms can be verified similarly, and all hold true for $\mathbb{R}^2$, so it is a **vector space**.

---

### 🚫 Non-Example:

Let’s define a set:

$$
W = \left\{ \begin{bmatrix} x \\ y \end{bmatrix} \in \mathbb{R}^2 \mid x + y = 1 \right\}
$$

This **is not** a vector space because:

- It’s not closed under addition:

  $$
  \begin{bmatrix} 1 \\ 0 \end{bmatrix} + \begin{bmatrix} 0 \\ 1 \end{bmatrix} = \begin{bmatrix} 1 \\ 1 \end{bmatrix} \quad \text{(but } 1 + 1 \neq 1\text{)}
  $$

So it **violates the closure axiom**, and thus is **not** a vector space.

---

### 🎓 Summary

| Concept          | Description                                                        |
| ---------------- | ------------------------------------------------------------------ |
| **Vector**       | An ordered list of numbers (elements)                              |
| **Vector Space** | A set of vectors that obey 10 algebraic rules                      |
| **Operations**   | Vector addition and scalar multiplication                          |
| **Example**      | $\mathbb{R}^2, \mathbb{R}^3, \mathbb{R}^n$                         |
| **Non-example**  | Any set that breaks even one rule (like not closed under addition) |

---

## <span style="color:#ff0054" id="t4">**What is Field?**</span>

### 🔷 What is a Field (in Mathematics)?

A **field** is a **set of numbers** (or elements) with two operations:

1. **Addition**
2. **Multiplication**

These operations must follow certain **rules (axioms)** — similar to how numbers work in regular arithmetic.

---

### ✅ **Examples of Fields**

- $\mathbb{R}$: The set of **real numbers**
- $\mathbb{Q}$: The set of **rational numbers**
- $\mathbb{C}$: The set of **complex numbers**
- $\mathbb{Z}_p$: The set of integers modulo $p$, where $p$ is a **prime number** (used in finite fields)

> Most of linear algebra is done over the field $\mathbb{R}$ or $\mathbb{C}$.

---

### 🧮 What Rules Must a Field Follow?

A field is a set $F$ with two operations: **addition** (+) and **multiplication** (×), such that:

### ➕ Addition rules:

1. **Closure**: $a + b \in F$
2. **Commutative**: $a + b = b + a$
3. **Associative**: $(a + b) + c = a + (b + c)$
4. **Additive identity**: There exists 0 such that $a + 0 = a$
5. **Additive inverse**: For every $a \in F$, there exists $-a$ such that $a + (-a) = 0$

### ✖️ Multiplication rules:

6. **Closure**: $a \cdot b \in F$
7. **Commutative**: $a \cdot b = b \cdot a$
8. **Associative**: $(a \cdot b) \cdot c = a \cdot (b \cdot c)$
9. **Multiplicative identity**: There exists 1 (≠ 0) such that $a \cdot 1 = a$
10. **Multiplicative inverse**: For every non-zero $a \in F$, there exists $a^{-1}$ such that $a \cdot a^{-1} = 1$

### 🔄 Distributive law:

11. **Distributivity**: $a \cdot (b + c) = a \cdot b + a \cdot c$

---

### 🔑 Summary

| Term         | Meaning                                                                                                    |
| ------------ | ---------------------------------------------------------------------------------------------------------- |
| **Field**    | A set where you can add, subtract, multiply, and divide (except by 0), and all arithmetic behaves "nicely" |
| **Examples** | Real numbers ($\mathbb{R}$), Complex numbers ($\mathbb{C}$), Rational numbers ($\mathbb{Q}$)               |
| **Used in**  | Vector spaces, matrices, linear equations, coding theory, cryptography                                     |

---

### 🔍 Example: Real Numbers $\mathbb{R}$

Let’s check:

- $2 + 3 = 5 \in \mathbb{R}$ ✅
- $2 \cdot 3 = 6 \in \mathbb{R}$ ✅
- Every non-zero real number has an inverse: $\frac{1}{2} \in \mathbb{R}$ ✅
  So $\mathbb{R}$ is a **field**.

---

Excellent question! **Linear Algebra** is one of the foundational pillars of **Machine Learning (ML)**. It provides the mathematical framework to represent and manipulate data, models, and algorithms.

Let me break it down clearly with **real-world ML connections** 👇

---

## 🔷 <span style="color:#ff0054" id="t5">**Why is Linear Algebra important in ML?**</span>

At its core, **machine learning is about data and transformations** — and both can be represented using **vectors**, **matrices**, and **linear operations**.

---

### 🔑 Core Linear Algebra Concepts in ML

| Linear Algebra Concept                 | ML Equivalent or Use Case                                                 |
| -------------------------------------- | ------------------------------------------------------------------------- |
| **Vector**                             | Data point or feature vector                                              |
| **Matrix**                             | Dataset (rows = samples, columns = features)                              |
| **Matrix Multiplication**              | Linear transformation, weights applied to inputs                          |
| **Dot product**                        | Similarity between vectors (used in cosine similarity, projections, etc.) |
| **Transpose**                          | Changing orientation of data (e.g., row ↔ column format)                  |
| **Determinant, Rank**                  | Invertibility, feature independence                                       |
| **Eigenvalues & Eigenvectors**         | PCA (dimensionality reduction), stability analysis                        |
| **Norms**                              | Measuring vector magnitudes (used in loss functions, regularization)      |
| **Singular Value Decomposition (SVD)** | Dimensionality reduction, recommender systems                             |

---

### 📦 Application Areas in Machine Learning

### 1. **Data Representation**

Each data point is represented as a **vector**:

$$
\text{Input: } \vec{x} = \begin{bmatrix} x_1 \\ x_2 \\ \cdots \\ x_n \end{bmatrix}
$$

The entire dataset is represented as a **matrix**:

$$
X = \begin{bmatrix}
x_{11} & x_{12} & \cdots & x_{1n} \\
x_{21} & x_{22} & \cdots & x_{2n} \\
\vdots & \vdots & \ddots & \vdots \\
x_{m1} & x_{m2} & \cdots & x_{mn}
\end{bmatrix}
$$

### 2. **Linear Regression**

One of the simplest ML models is **Linear Regression**, represented in matrix form:

$$
\hat{y} = X\vec{w}
$$

Where:

- $X$: feature matrix
- $\vec{w}$: weight vector (model parameters)
- $\hat{y}$: predicted outputs

### 3. **Gradient Descent (Optimization)**

Linear algebra is used to compute gradients, updates to weights:

$$
\vec{w}_{\text{new}} = \vec{w} - \alpha \nabla J(\vec{w})
$$

Where:

- $\nabla J(\vec{w})$ is the **gradient vector**
- $\alpha$: learning rate

### 4. **Neural Networks**

Each layer of a neural network performs:

$$
\text{Output} = \sigma(W \cdot \vec{x} + \vec{b})
$$

- $W$: weight matrix
- $\vec{x}$: input vector
- $\vec{b}$: bias vector
- $\sigma$: activation function

### 5. **Principal Component Analysis (PCA)**

Used for dimensionality reduction:

- Uses **eigenvectors** and **eigenvalues** of the **covariance matrix**
- Finds directions (principal components) that **maximize variance**

### 6. **Support Vector Machines (SVMs)**

- Use dot products for computing decision boundaries
- Optimization involves solving systems of equations (linear algebra)

### 7. **Natural Language Processing (NLP)**

- Words are converted into **vectors** (Word2Vec, GloVe)
- Similarity of meaning = **cosine similarity** (dot product of normalized vectors)

---

### 🧠 Quick Intuition

| Linear Algebra Tool | ML Analogy                                       |
| ------------------- | ------------------------------------------------ |
| Vector              | A single data point or weight                    |
| Matrix              | A dataset or neural net layer                    |
| Matrix product      | Applying weights to inputs                       |
| Eigen decomposition | Compressing or rotating data                     |
| Norm                | Size of error or weight (used in loss functions) |

---

### ✅ Summary

Linear Algebra is everywhere in ML:

- **Represents data**
- **Builds models**
- **Optimizes performance**
- **Extracts features**
- **Reduces dimensions**

---
