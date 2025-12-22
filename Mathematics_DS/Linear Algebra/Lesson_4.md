# <span style="color:#a4ac86">**Lesson-4 Vector Multiplication**</span>

## <span style="color:#a7c957">Table of Contents</span>

- [Vector Multiplication & Types](#t1)
- [Application of Vector Addition in ML](#t2)
- [Numerical](#t3)

## <span style="color:#ff0054" id="t1">**Vector Multiplication & Types**</span>

### ✅ 1. **Dot Product (Inner Product)**

### 📌 Definition:

The **dot product** of two vectors $\vec{a}$ and $\vec{b}$ of the same size:

$$
\vec{a} \cdot \vec{b} = \sum_{i=1}^{n} a_i \cdot b_i
$$

### 💡 Result:

A **scalar (single number)**

### 🧠 Intuition:

Measures the **similarity** or **alignment** between two vectors.

### 🧮 Example:

Let $\vec{a} = [2, 3]$, $\vec{b} = [4, 5]$:

$$
\vec{a} \cdot \vec{b} = 2 \cdot 4 + 3 \cdot 5 = 8 + 15 = \boxed{23}
$$

### 🔍 Properties:

- **Commutative**: $\vec{a} \cdot \vec{b} = \vec{b} \cdot \vec{a}$
- **Distributive**: $\vec{a} \cdot (\vec{b} + \vec{c}) = \vec{a} \cdot \vec{b} + \vec{a} \cdot \vec{c}$
- **Associates with scalar**: $c(\vec{a} \cdot \vec{b}) = (c\vec{a}) \cdot \vec{b}$

### ✅ Application in ML:

- Linear regression: $\vec{w}^\top \vec{x}$
- Neural nets: weighted sum of inputs
- Cosine similarity: $\cos \theta = \frac{\vec{a} \cdot \vec{b}}{||\vec{a}||\cdot||\vec{b}||}$

---

### ✅ 2. **Element-wise Multiplication (Hadamard Product)**

### 📌 Definition:

Multiply corresponding elements:

$$
\vec{a} \circ \vec{b} = [a_1b_1, a_2b_2, ..., a_nb_n]
$$

### 💡 Result:

A **vector** of same length

### 🧮 Example:

Let $\vec{a} = [2, 3]$, $\vec{b} = [4, 5]$:

$$
\vec{a} \circ \vec{b} = [2 \cdot 4, 3 \cdot 5] = [8, 15]
$$

### 🔍 Properties:

- **Element-wise**: works index-by-index
- **Not commutative in deep learning**: order may matter when broadcasting

### ✅ Application in ML:

- Used in attention mechanisms
- Dropout masks
- Feature-wise scaling
- Gate operations in LSTMs/GRUs

---

### ✅ 3. **Scalar Multiplication**

### 📌 Definition:

Multiply **each element of a vector** by a scalar $c$:

$$
c \cdot \vec{a} = [c \cdot a_1, c \cdot a_2, ..., c \cdot a_n]
$$

### 💡 Result:

A **vector**

### 🧮 Example:

Let $\vec{a} = [2, 3]$, $c = 4$:

$$
4 \cdot \vec{a} = [8, 12]
$$

### 🔍 Properties:

- Distributive: $c(\vec{a} + \vec{b}) = c\vec{a} + c\vec{b}$
- Associative with scalar: $(cd)\vec{a} = c(d\vec{a})$

### ✅ Application in ML:

- Weight updates: $\vec{w} = \vec{w} - \alpha \cdot \nabla J(\vec{w})$
- Learning rate scaling
- Feature scaling/normalization

---

### ✅ 4. **Cross Product (only in 3D)**

### 📌 Definition:

The **cross product** of two 3D vectors $\vec{a} \times \vec{b}$ results in a new vector that is **orthogonal** (perpendicular) to both.

$$
\vec{a} \times \vec{b} =
\begin{bmatrix}
a_2b_3 - a_3b_2 \\
a_3b_1 - a_1b_3 \\
a_1b_2 - a_2b_1
\end{bmatrix}
$$

### 💡 Result:

A **vector in 3D**

### 🧮 Example:

Let $\vec{a} = [1, 2, 3], \vec{b} = [4, 5, 6]$

$$
\vec{a} \times \vec{b} =
\begin{bmatrix}
(2)(6)-(3)(5) \\
(3)(4)-(1)(6) \\
(1)(5)-(2)(4)
\end{bmatrix}
=
\begin{bmatrix}
12-15 \\
12-6 \\
5-8
\end{bmatrix}
= [-3, 6, -3]
$$

### 🔍 Properties:

- **Anticommutative**: $\vec{a} \times \vec{b} = -(\vec{b} \times \vec{a})$
- Only defined in 3D
- Result vector is orthogonal to both inputs

### ✅ Application in ML/AI:

- 3D computer vision (camera orientation)
- Robotics (angular velocity, torque)
- Physics simulations in game AI

---

### 📊 Summary Table:

| Type                        | Operands         | Result      | ML Application                      |
| --------------------------- | ---------------- | ----------- | ----------------------------------- |
| **Dot Product**             | 2 same-sized vec | Scalar      | Similarity, regression, projections |
| **Element-wise (Hadamard)** | 2 same-sized vec | Vector      | LSTM gates, attention, dropout      |
| **Scalar Multiplication**   | Scalar × Vector  | Vector      | Learning rate scaling, optimization |
| **Cross Product**           | 2 vectors in 3D  | Vector (3D) | Computer vision, robotics           |

---
