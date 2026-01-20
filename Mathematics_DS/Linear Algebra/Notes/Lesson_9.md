<span style="color:orange; font-size:26px; font-weight:bold;">Subspace — Explained from First Principles</span>

**Navigation**

1. <a href="#what"><span style="color:red;">What is a subspace (intuition)</span></a>
2. <a href="#makes"><span style="color:red;">What makes a vector space a subspace</span></a>
3. <a href="#test"><span style="color:red;">How to check whether something is a subspace (test)</span></a>
4. <a href="#solved"><span style="color:red;">Solved examples (subspace & not a subspace)</span></a>
5. <a href="#math"><span style="color:red;">Mathematical representation of a subspace</span></a>
6. <a href="#ml"><span style="color:red;">Uses of subspace concept in ML / AI</span></a>

---

<span id="what" style="color:red; font-size:20px; font-weight:bold;">1. What is a subspace (intuition)</span>

From first principles:

> A **subspace** is a **smaller vector space living inside a bigger vector space**.

Think geometrically:

- ℝ³ is a full 3D space
- A plane through the origin inside ℝ³ is a **subspace**
- A line through the origin is also a **subspace**

Key intuition:

> A subspace must **behave exactly like a vector space**, just with fewer directions.

---

<span id="makes" style="color:red; font-size:20px; font-weight:bold;">2. What makes a vector space a subspace</span>

Let:

- V = a vector space
- W ⊆ V (W is a subset of V)

Then **W is a subspace of V if and only if**:

### 🔴 Core principle

> **W itself must be a vector space using the same operations as V**

This leads to **three essential conditions** (derived from first principles).

---

<span id="test" style="color:red; font-size:20px; font-weight:bold;">3. How to check whether something is a subspace (subspace test)</span>

Instead of checking all 8 axioms again, we use a **minimal test**.

A subset W of V is a subspace **iff**:

### ✅ Condition 1: Zero vector

0 ∈ W

Why?

- Vector space must contain identity
- No zero → no vector space

---

### ✅ Condition 2: Closure under addition

If u, v ∈ W ⇒ u + v ∈ W

Why?

- Adding vectors should not escape the set

---

### ✅ Condition 3: Closure under scalar multiplication

If v ∈ W and a ∈ ℝ ⇒ av ∈ W

Why?

- Scaling should stay inside the set

---

📌 If **any one fails** → **NOT a subspace**

---

<span id="solved" style="color:red; font-size:20px; font-weight:bold;">4. Solved examples</span>

### ✔️ Example 1: Plane through origin in ℝ³

W = { (x, y, z) ∈ ℝ³ | x + y + z = 0 }

#### Check conditions:

**Zero vector**
(0,0,0): 0+0+0=0 ✔

**Addition**
u = (x₁,y₁,z₁), v = (x₂,y₂,z₂)
Both satisfy equation

u + v = (x₁+x₂, y₁+y₂, z₁+z₂)
(x₁+x₂)+(y₁+y₂)+(z₁+z₂)=0 ✔

**Scalar multiplication**
a·u = (ax₁, ay₁, az₁)
a(x₁+y₁+z₁)=a·0=0 ✔

➡ **Subspace**

---

### ❌ Example 2: Plane NOT through origin

W = { (x,y,z) | x + y + z = 1 }

**Zero vector?**
(0,0,0): sum = 0 ≠ 1 ❌

➡ **NOT a subspace**

📌 Any shift away from origin destroys subspace structure.

---

### ❌ Example 3: Positive quadrant in ℝ²

W = { (x,y) | x ≥ 0, y ≥ 0 }

Scalar multiplication with −1:
−1·(1,2) = (−1,−2) ∉ W ❌

➡ **NOT a subspace**

---

<span id="math" style="color:red; font-size:20px; font-weight:bold;">5. Mathematical representation of a subspace</span>

From first principles, a subspace is described in **three equivalent ways**.

---

### 🔹 1. Span of vectors

W = span{v₁, v₂, …, vₖ}

Meaning:

> All linear combinations of given vectors

Example:
span{ (1,0,0), (0,1,0) }
→ xy-plane in ℝ³

---

### 🔹 2. Solution space of linear equations

Ax = 0

All solutions form a subspace.

Why?

- Always contains zero
- Closed under addition & scaling

---

### 🔹 3. Column space / row space

Given matrix A:

- Column space = subspace of ℝᵐ
- Row space = subspace of ℝⁿ

Dimension = rank(A)

---

<span id="ml" style="color:red; font-size:20px; font-weight:bold;">6. Uses of subspace concept in ML / AI</span>

From first principles:

ML = finding **useful lower-dimensional structure** inside high-dimensional data.

That is exactly a **subspace problem**.

---

### 🔹 PCA (Principal Component Analysis)

Finds a **low-dimensional subspace** that:

- Preserves maximum variance
- Removes redundant directions

---

### 🔹 Feature selection & representation learning

Useful features lie in a **subspace of original feature space**

Noise directions are discarded.

---

### 🔹 Linear models

Predictions lie in:

> column space of feature matrix

Understanding subspaces tells:

- what models can/cannot learn

---

### 🔹 Neural networks

Hidden layers learn:

- intermediate **representation subspaces**

---

### 🔹 Embeddings (NLP / Vision)

Words/images lie in **semantic subspaces**

- similarity = closeness in subspace

---

## ✅ Final first-principle takeaway

> **A subspace is a subset of a vector space that itself behaves like a vector space—closed under addition and scaling and anchored at the origin.**

---

<span style="color:orange; font-size:26px; font-weight:bold;">Why a Vector Space (or Subspace) Must Contain the Zero Vector — Explained from First Principles</span>

**Navigation**

1. <a href="#fp"><span style="color:red;">First-principle intuition: what “space” really means</span></a>
2. <a href="#identity"><span style="color:red;">Why addition needs an identity element</span></a>
3. <a href="#scaling"><span style="color:red;">Why scalar multiplication forces the zero vector</span></a>
4. <a href="#inverses"><span style="color:red;">Why additive inverses imply zero</span></a>
5. <a href="#nospace"><span style="color:red;">Why any set without zero cannot be a vector space</span></a>
6. <a href="#subspace"><span style="color:red;">Why subspaces MUST contain the same zero vector</span></a>
7. <a href="#ml"><span style="color:red;">ML / AI intuition: why zero matters in practice</span></a>

---

<span id="fp" style="color:red; font-size:20px; font-weight:bold;">1. First-principle intuition: what “space” really means</span>

From first principles, a **vector space** is designed to model:

> _displacement, direction, and combination of effects_

To do this meaningfully, we must answer:

- What does it mean to **add nothing**?
- What does it mean to **scale to nothing**?

That “nothing” is the **zero vector**.

Without it, the concept of **vector arithmetic collapses**.

---

<span id="identity" style="color:red; font-size:20px; font-weight:bold;">2. Why addition needs an identity element</span>

Addition is a fundamental operation in a vector space.

From first principles of algebra:

> Every meaningful addition system needs an **identity element**

An identity element `e` satisfies:

```
v + e = v
```

In vector spaces, this identity must be:

```
(0, 0, 0, ..., 0)
```

Why?

- Adding “no displacement” should not change displacement
- Adding “no force” should not change force

So:

> **The zero vector is the only candidate for additive identity**

---

<span id="scaling" style="color:red; font-size:20px; font-weight:bold;">3. Why scalar multiplication forces the zero vector</span>

Now think from first principles about **scaling**.

If `v` is a vector and `0` is a scalar, then:

```
0 · v = ?
```

Physically:

- Scale a displacement by 0
- Scale a force by 0

Result must be:

```
no displacement → zero vector
```

This is **not a choice**, it is forced by meaning.

Therefore:

> If scalar multiplication is allowed, the zero vector must exist.

---

<span id="inverses" style="color:red; font-size:20px; font-weight:bold;">4. Why additive inverses imply zero</span>

Vector spaces require:

> For every vector `v`, there exists `-v` such that:

```
v + (-v) = 0
```

This rule is meaningless unless **0 already exists**.

So:

- Inverses cannot exist without zero
- Cancellation cannot exist without zero

Hence:

> **Zero vector is required for symmetry and reversibility**

---

<span id="nospace" style="color:red; font-size:20px; font-weight:bold;">5. Why any set without zero cannot be a vector space</span>

Consider this set:

```
W = { (x, y) ∈ ℝ² | x + y = 1 }
```

Check:

- (0,0) ∉ W ❌

Now see what breaks:

Take v = (1,0) ∈ W
Take scalar 0:

```
0 · v = (0,0) ∉ W
```

So:

- Scalar multiplication is **not closed**
- Additive inverse cannot exist
- Identity element is missing

This set **cannot behave like a space**.

➡ **Not a vector space**

---

<span id="subspace" style="color:red; font-size:20px; font-weight:bold;">6. Why subspaces MUST contain the same zero vector</span>

A **subspace** must:

- use the same operations
- obey the same algebra

If W ⊆ V is a subspace, then:

```
0 · v = 0 ∈ W
```

So:

> Every subspace must contain the **same zero vector as the parent space**

This is why:

- Lines and planes must pass through the origin
- Shifted planes are **not** subspaces

---

<span id="ml" style="color:red; font-size:20px; font-weight:bold;">7. ML / AI intuition: why zero matters in practice</span>

### 🔹 Optimization

Zero vector = **no signal / no gradient**

Without it:

- convergence logic fails
- learning rules break

---

### 🔹 Feature spaces

Zero vector = **absence of all features**

Used in:

- sparse representations
- NLP bag-of-words
- embeddings

---

### 🔹 Regularization

Zero vector is the **neutral solution**

L1, L2 penalties pull parameters toward zero.

---

## ✅ Final first-principle takeaway

> **The zero vector is not an optional rule — it is the logical anchor that makes addition, scaling, cancellation, and learning possible. Any structure without it cannot function as a vector space.**

---
