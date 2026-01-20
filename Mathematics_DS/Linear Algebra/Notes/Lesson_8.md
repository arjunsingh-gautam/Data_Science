<span style="color:orange; font-size:26px; font-weight:bold;">Vector Space — Explained from First Principles</span>

**Navigation**

1. <a href="#what"><span style="color:red;">What is a vector space (intuition first)</span></a>
2. <a href="#set"><span style="color:red;">Is it just a set of vectors? (why rules matter)</span></a>
3. <a href="#rules"><span style="color:red;">Rules (axioms) a set must follow — with examples</span></a>
4. <a href="#notvs"><span style="color:red;">Example of something that is NOT a vector space</span></a>
5. <a href="#math"><span style="color:red;">Mathematical representation & dimension</span></a>
6. <a href="#ml"><span style="color:red;">Uses of vector spaces in ML / AI (first-principle view)</span></a>
7. <a href="#impl"><span style="color:red;">Implementing vector spaces in Python / NumPy</span></a>

---

<span id="what" style="color:red; font-size:20px; font-weight:bold;">1. What is a vector space (intuition first)</span>

From first principles:

> A **vector space** is a **world of objects** where
> • you can **add** objects,
> • you can **scale** them,
> • and doing these operations **never takes you outside the world**.

This “world” behaves **consistently** under addition and scaling.

So the core question is not _what objects are_, but:

> **How do they behave under operations?**

---

<span id="set" style="color:red; font-size:20px; font-weight:bold;">2. Is it just a set of vectors? (why rules matter)</span>

Yes — **a vector space is a set**.
But **not every set of vectors is a vector space**.

Why?

Because mathematics cares about **structure**, not just membership.

A set becomes a **vector space only if**:

- vector addition works properly
- scalar multiplication works properly
- the set is **closed** under these operations

So:

> **Vector space = set + rules (axioms)**

---

<span id="rules" style="color:red; font-size:20px; font-weight:bold;">3. Rules (axioms) a set must follow — with examples</span>

Let **V** be a set and **a, b** be real numbers (scalars).

### 🔹 Rule 1: Closure under addition

If u, v ∈ V ⇒ u + v ∈ V

Example:
ℝ²
(1,2) + (3,4) = (4,6) ∈ ℝ² ✔

---

### 🔹 Rule 2: Closure under scalar multiplication

If v ∈ V and a ∈ ℝ ⇒ av ∈ V

Example:
2·(1,2) = (2,4) ∈ ℝ² ✔

---

### 🔹 Rule 3: Additive identity (zero vector)

There exists **0 ∈ V** such that:
v + 0 = v

Example:
0 = (0,0)

---

### 🔹 Rule 4: Additive inverse

For every v ∈ V, there exists −v ∈ V

Example:
v = (1,2) ⇒ −v = (−1,−2)

---

### 🔹 Rule 5: Associativity of addition

(u + v) + w = u + (v + w)

---

### 🔹 Rule 6: Commutativity of addition

u + v = v + u

---

### 🔹 Rule 7: Distributive laws

a(u + v) = au + av
(a + b)v = av + bv

---

### 🔹 Rule 8: Scalar identity

1·v = v

---

📌 **If ALL rules are satisfied → vector space**
📌 **Fail even one → not a vector space**

---

<span id="notvs" style="color:red; font-size:20px; font-weight:bold;">4. Example of something that is NOT a vector space</span>

### ❌ Example: Set of all 2D vectors with only positive components

V = { (x, y) | x > 0, y > 0 }

Check rules:

- (1,2) ∈ V ✔
- Scalar multiplication with −1:

−1·(1,2) = (−1, −2) ∉ V ❌

Fails **additive inverse rule**.

➡ **Not a vector space**

---

### ❌ Example: Integers ℤ as vectors over real numbers

2 ∈ ℤ
0.5 · 2 = 1 ✔
0.3 · 2 = 0.6 ∉ ℤ ❌

Fails **closure under scalar multiplication**.

---

<span id="math" style="color:red; font-size:20px; font-weight:bold;">5. Mathematical representation & dimension</span>

A vector space is written as:

V over ℝ (or ℂ)

Examples:

- ℝ² → 2D vector space
- ℝⁿ → n-dimensional vector space
- Polynomial space P₂
- Function space f(x)

---

### 🔹 What is dimension?

From first principles:

> **Dimension = number of independent directions needed to span the space**

Examples:

- ℝ² → dimension 2
- ℝ³ → dimension 3

Formally:

> Dimension = size of a **basis** (maximal linearly independent set)

---

### 🔹 How we know vector dimension

Vector:
(1,2,3,4)

Dimension = 4
Because 4 components → lives in ℝ⁴

---

<span id="ml" style="color:red; font-size:20px; font-weight:bold;">6. Uses of vector spaces in ML / AI (first-principle view)</span>

From first principles:

ML = **geometry + optimization**

### 🔹 Data as vectors

Each data point = vector
Each feature = dimension

Example:

```
[age, income, credit_score]
```

→ vector in ℝ³

---

### 🔹 Feature space

All data points together form a **vector space**

Linear models:

- learn **directions** in this space

---

### 🔹 Embeddings (NLP, Vision)

Words, images → vectors in high-dimensional spaces

Similarity = distance / angle in vector space

---

### 🔹 PCA & dimensionality reduction

Find **important subspaces**
Remove redundant directions

---

### 🔹 Neural networks

Each layer:

- linear transformation (vector space → vector space)
- non-linear warp

---

<span id="impl" style="color:red; font-size:20px; font-weight:bold;">7. Implementing vector spaces in Python / NumPy</span>

### 🔹 Vectors

```python
import numpy as np

v = np.array([1, 2, 3])
u = np.array([4, 5, 6])
```

---

### 🔹 Vector addition (closure)

```python
v + u
```

---

### 🔹 Scalar multiplication

```python
2 * v
```

---

### 🔹 Zero vector

```python
np.zeros(3)
```

---

### 🔹 Span & dimension (rank)

```python
matrix = np.array([
    [1, 0],
    [0, 1],
    [1, 1]
]).T

np.linalg.matrix_rank(matrix)
```

Rank = dimension of span

---

## ✅ Final first-principle takeaway

> **A vector space is not about “vectors”, but about a set of objects that behaves consistently under addition and scaling, enabling geometry, learning, and reasoning in ML/AI.**

---
