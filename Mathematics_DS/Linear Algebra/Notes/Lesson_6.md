<span style="color:orange; font-size:26px; font-weight:bold;">Linearly Independent Vectors — Explained from First Principles</span>

**Navigation**

1. <a href="#def"><span style="color:red;">What are linearly independent vectors?</span></a>
2. <a href="#set"><span style="color:red;">Why linear independence applies to a set of vectors</span></a>
3. <a href="#core"><span style="color:red;">First-principle definition (core idea)</span></a>
4. <a href="#conditions"><span style="color:red;">Conditions for vectors to be linearly independent</span></a>
5. <a href="#min"><span style="color:red;">Minimum condition for linear independence</span></a>
6. <a href="#max"><span style="color:red;">Maximum condition (geometric meaning)</span></a>
7. <a href="#example"><span style="color:red;">Numeric example (step-by-step)</span></a>

---

<span id="def" style="color:red; font-size:20px; font-weight:bold;">1. What are linearly independent vectors?</span>

From **first principles**, vectors represent **directions in space**.

A set of vectors is called **linearly independent** if **every vector contributes a new, unique direction** that cannot be obtained from the others.

In simple words:

> **No vector in the set is redundant.**

If you remove even one vector, the space spanned by the set **shrinks**.

---

<span id="set" style="color:red; font-size:20px; font-weight:bold;">2. Why linear independence applies to a set of vectors</span>

Independence is about **mutual non-reliance**.

- One vector alone cannot be “independent of others”
- Independence only makes sense when **comparison exists**

Therefore:

> **Linear independence is a property of a set of vectors, not a single vector.**

---

<span id="core" style="color:red; font-size:20px; font-weight:bold;">3. First-principle definition (core idea)</span>

Consider vectors:

v₁, v₂, v₃, … , vₙ

Form this equation:

a₁v₁ + a₂v₂ + a₃v₃ + … + aₙvₙ = 0

Now ask:

👉 Can the zero vector be produced **without forcing all coefficients to be zero**?

### If the answer is NO:

a₁ = a₂ = … = aₙ = 0 is the **only** solution
➡ vectors are **linearly independent**

This is the **purest mathematical definition**.

---

<span id="conditions" style="color:red; font-size:20px; font-weight:bold;">4. Conditions for vectors to be linearly independent</span>

A set of vectors is linearly independent **if and only if**:

1. No vector can be written as a linear combination of others
2. No vector is a scalar multiple of another
3. The equation
   a₁v₁ + a₂v₂ + … + aₙvₙ = 0
   has **only the trivial solution**
4. Number of vectors ≤ dimension of the space

All conditions express the same first-principle idea:

> **Each vector adds a new dimension.**

---

<span id="min" style="color:red; font-size:20px; font-weight:bold;">5. Minimum condition for linear independence</span>

The **minimum requirement** is:

> **Not even a single vector in the set can be represented as a linear combination of the remaining vectors.**

If **one** vector becomes expressible,
the entire set **collapses into dependence**.

So independence is **fragile**:

- One redundancy → independence destroyed

---

<span id="max" style="color:red; font-size:20px; font-weight:bold;">6. Maximum condition (geometric meaning)</span>

The **maximum condition** is reached when:

> The number of linearly independent vectors equals the **dimension of the space**

Examples:

- 2 independent vectors → plane (2D)
- 3 independent vectors → space (3D)

Beyond this:

- Adding more vectors **forces dependence**

So:

> Linear independence defines the **maximum number of directions possible in a space**.

---

<span id="example" style="color:red; font-size:20px; font-weight:bold;">7. Numeric example (step-by-step)</span>

Consider vectors in 2D:

v₁ = (1, 0)
v₂ = (0, 1)

---

### Step 1: Try scalar multiples

v₂ ≠ k·v₁ for any scalar k
✔️ passes

---

### Step 2: Try linear combination

Can we write:

v₂ = a·v₁ ?

(0,1) ≠ a·(1,0)
✔️ impossible

---

### Step 3: Zero-vector test

a₁(1,0) + a₂(0,1) = (0,0)

This gives:
a₁ = 0
a₂ = 0

Only trivial solution exists ✔️

---

### Final conclusion

The set { (1,0), (0,1) } is **linearly independent** because:

- Each vector adds a unique direction
- Together they fully span 2D space

---

### One-line first-principle takeaway

> **Linearly independent vectors are those where no vector can be generated from the others, and each contributes a genuinely new dimension to the space.**

---
