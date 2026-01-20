<span style="color:orange; font-size:26px; font-weight:bold;">Basis of a Vector Space — Explained from First Principles</span>

**Navigation**

1. <a href="#what"><span style="color:red;">What is a basis of a vector space</span></a>
2. <a href="#size"><span style="color:red;">Why the number of basis vectors equals the dimension</span></a>
3. <a href="#check"><span style="color:red;">How to determine whether a set of vectors is a basis</span></a>
4. <a href="#example"><span style="color:red;">Solved mathematical example</span></a>
5. <a href="#standard"><span style="color:red;">Standard basis & relation with unit vectors</span></a>
6. <a href="#ml"><span style="color:red;">Importance of basis in ML / AI</span></a>

---

<span id="what" style="color:red; font-size:20px; font-weight:bold;">1. What is a basis of a vector space</span>

From **first principles**, a vector space is about:

- **directions** (independence)
- **reachability** (span)

A **basis** is the smallest possible set of vectors that:

1. **Spans the entire vector space**
2. Is **linearly independent**

So:

> **A basis is a minimal, non-redundant generating set of a vector space.**

Formally, a set
[
{v_1, v_2, \dots, v_k}
]
is a basis of vector space (V) if:

- ( \text{span}{v_1,\dots,v_k} = V )
- The vectors are linearly independent

---

<span id="size" style="color:red; font-size:20px; font-weight:bold;">2. Why the number of basis vectors equals the dimension</span>

From first principles:

- Each **linearly independent vector adds one new degree of freedom**
- You cannot describe more degrees of freedom than the space allows

This leads to a fundamental property:

> **All bases of a vector space have the same number of vectors.**

That number is called the **dimension** of the vector space.

---

### Can a vector space have “multiple” bases?

Yes — **infinitely many**.

But:

- Every basis has the **same number of vectors**
- That number = **dimension of the space**

---

### Solved mathematical example

Consider ( \mathbb{R}^2 )

Basis 1:
[
{(1,0), (0,1)}
]

Basis 2:
[
{(1,1), (1,-1)}
]

Check:

- Both sets have **2 linearly independent vectors**
- Both span ( \mathbb{R}^2 )

➡ Both are valid bases
➡ Dimension of ( \mathbb{R}^2 = 2 )

This shows:

> **Basis is not unique, dimension is.**

---

<span id="check" style="color:red; font-size:20px; font-weight:bold;">3. How to determine whether a set of vectors is a basis</span>

From first principles, a set of vectors is a **basis iff**:

### ✅ Condition 1: Linear independence

No vector can be written as a linear combination of others.

### ✅ Condition 2: Spanning

Every vector in the space can be written as a linear combination of them.

---

### Practical shortcut (very important)

For a vector space of dimension (n):

> **If a set has exactly (n) vectors, then:**

- If they are linearly independent → they automatically span
- If they span → they are automatically independent

This is a deep structural property of vector spaces.

---

<span id="example" style="color:red; font-size:20px; font-weight:bold;">4. Solved example: checking if a set is a basis</span>

### Example: Is

[
{(1,2), (3,6)}
]
a basis of ( \mathbb{R}^2 )?

#### Step 1: Check independence

[
(3,6) = 3(1,2)
]

Vectors are linearly dependent ❌

➡ **Not a basis**

---

### Example: Is

[
{(1,2), (2,1)}
]
a basis of ( \mathbb{R}^2 )?

#### Step 1: Check independence

Solve:
[
a(1,2) + b(2,1) = (0,0)
]

This gives:
[
a + 2b = 0 \
2a + b = 0
]

Only solution: (a=b=0) ✔

#### Step 2: Number of vectors = dimension

2 vectors in ( \mathbb{R}^2 )

➡ Independent ⇒ spans automatically

➡ **This set is a basis**

---

<span id="standard" style="color:red; font-size:20px; font-weight:bold;">5. Standard basis & relation with unit vectors</span>

### What is the standard basis?

The **standard basis** of ( \mathbb{R}^n ) is:

[
e_1 = (1,0,0,\dots,0) \
e_2 = (0,1,0,\dots,0) \
\vdots \
e_n = (0,0,0,\dots,1)
]

These vectors:

- Are **linearly independent**
- Span the entire space
- Align with coordinate axes

---

### Relation with unit vectors

Each standard basis vector:

- Has magnitude 1
- Points along exactly one axis

So:

> **Standard basis vectors are unit vectors along coordinate axes.**

Every vector:
[
v = (x_1, x_2, \dots, x_n)
]
can be written as:
[
v = x_1 e_1 + x_2 e_2 + \dots + x_n e_n
]

---

<span id="ml" style="color:red; font-size:20px; font-weight:bold;">6. Importance of basis in ML / AI</span>

From first principles:

ML = **representing data + learning transformations**

Basis answers:

> _In which directions does my data actually live?_

---

### 🔹 Feature representation

- Each feature acts like a basis direction
- Changing basis = changing representation

---

### 🔹 PCA

- Finds a **new basis** aligned with maximum variance
- Old basis → rotated to a better one

---

### 🔹 Embeddings

- Words/images represented in learned bases
- Meaning encoded via coordinates in that basis

---

### 🔹 Model capacity

- Rank of feature matrix = size of basis
- Low-rank ⇒ fewer independent features ⇒ better generalization

---

### 🔹 Optimization

- Choice of basis affects:
  - conditioning
  - convergence speed
  - numerical stability

---

## ✅ Final first-principle takeaway

> **A basis is the minimal, non-redundant coordinate system of a vector space. While bases are not unique, their size is fixed and defines the dimension—making basis central to representation, learning, and generalization in ML/AI.**

---
