# <span style="color:darkcyan">**Numpy Array and Vectorised Operations**</span>

## 1. **Elementwise Arithmetic Operations**

Operate element by element on arrays of the same shape (or broadcastable).

### Syntax

```python
c = a + b
c = a - b
c = a * b
c = a / b
c = a ** b   # power
c = a % b    # modulo
```

### Example

```python
import numpy as np
a = np.array([1,2,3])
b = np.array([4,5,6])

print(a + b)   # [5 7 9]
print(a * b)   # [ 4 10 18]
print(a ** 2)  # [1 4 9]
```

### Use case

- Scaling data, normalization, feature engineering.

✅ **Best practice**: Always prefer vectorized operations over Python loops (much faster).

---

## 2. **Comparison Operations**

Elementwise comparison.

### Syntax

```python
a == b
a != b
a > b
a < b
a >= b
```

### Example

```python
print(a > 2)   # [False False  True]
```

### Use case

- Masking arrays for filtering (e.g., selecting values in a dataset).

✅ Use with **boolean indexing**:

```python
print(a[a > 1])  # [2 3]
```

---

## 3. **Logical Operations**

Elementwise AND, OR, NOT.

### Syntax

```python
np.logical_and(a, b)
np.logical_or(a, b)
np.logical_not(a)
```

### Example

```python
x = np.array([True, False, True])
y = np.array([False, False, True])

print(np.logical_and(x,y))  # [False False  True]
```

### Use case

- Filtering datasets with multiple conditions.

✅ Best practice: Avoid using `&`, `|` directly without parentheses (operator precedence can trick you).

---

## 4. **Aggregate / Reduction Operations**

Summarize arrays into a single value (or along axes).

### Syntax

```python
arr.sum(axis=None)
arr.mean(axis=None)
arr.max(axis=None)
arr.min(axis=None)
arr.std(axis=None)
arr.var(axis=None)
arr.prod(axis=None)   # product
```

### Example

```python
m = np.array([[1,2,3],[4,5,6]])
print(m.sum())        # 21
print(m.sum(axis=0))  # [5 7 9] (column sums)
print(m.mean(axis=1)) # [2. 5.] (row means)
```

### Use case

- Statistics (mean, std, var) → ML preprocessing.
- Aggregations in data analysis.

✅ Best practice: Always specify `axis` explicitly in ML pipelines for clarity.

---

## 5. **Linear Algebra Operations**

Use `np.dot`, `np.matmul`, `np.linalg`.

### Syntax

```python
np.dot(a,b)         # dot product
np.matmul(a,b)      # matrix multiplication
a @ b               # same as matmul
np.cross(a,b)       # cross product
np.linalg.inv(A)    # inverse
np.linalg.det(A)    # determinant
np.linalg.eig(A)    # eigenvalues, eigenvectors
```

### Example

```python
A = np.array([[1,2],[3,4]])
B = np.array([[5,6],[7,8]])

print(A @ B)             # matrix multiplication
print(np.dot([1,2,3], [4,5,6]))  # 32 (dot product)
```

### Use case

- Neural networks (matrix multiplications).
- PCA (eigenvalues).
- Solving linear equations.

✅ Best practice: Use `@` for readability instead of `np.dot` in ML code.

---

## 6. **Broadcasting Operations**

Allows operations between arrays of **different shapes** if rules allow.

### Example

```python
a = np.array([1,2,3])
b = 2
print(a * b)   # [2 4 6]

m = np.array([[1,2,3],[4,5,6]])
v = np.array([1,0,1])
print(m + v)   # [[2 2 4] [5 5 7]]
```

### Use case

- Adding bias term in NN layers.
- Normalizing each row/column.

✅ Best practice: Exploit broadcasting for performance, avoid `for` loops.

---

## 7. **Reshaping & Stacking Operations**

### Syntax

```python
arr.reshape(new_shape)
np.concatenate([a,b], axis=0)
np.vstack([a,b])
np.hstack([a,b])
np.split(arr, n)
```

### Example

```python
arr = np.arange(6).reshape(2,3)
print(np.vstack([arr, arr]))
print(np.hstack([arr, arr]))
```

### Use case

- Reshaping data for ML models.
- Stacking feature vectors.

---

## 8. **Universal Functions (ufuncs)**

Fast elementwise operations provided by NumPy.

### Syntax

```python
np.sqrt(a)
np.exp(a)
np.log(a)
np.sin(a)
np.cos(a)
np.tan(a)
```

### Example

```python
arr = np.array([1,4,9])
print(np.sqrt(arr))   # [1. 2. 3.]
```

### Use case

- Feature scaling, normalization.
- Scientific computing.

✅ Best practice: Use NumPy ufuncs instead of Python `math` module (faster, works on arrays).

---

## 9. **Cumulative Operations**

### Syntax

```python
arr.cumsum(axis=None)
arr.cumprod(axis=None)
```

### Example

```python
arr = np.array([1,2,3,4])
print(arr.cumsum())   # [1 3 6 10]
```

### Use case

- Running totals (finance, reinforcement learning).

---

## 10. **Clipping & Rounding**

### Syntax

```python
np.clip(arr, min_val, max_val)
np.round(arr, decimals=2)
np.floor(arr)
np.ceil(arr)
```

### Example

```python
arr = np.array([1.2, 3.7, -1.5])
print(np.clip(arr, 0, 2))  # [1.2 2.0 0.0]
```

### Use case

- Clipping gradient values in DL.
- Rounding for presentation.

---

## **Best Practices**

- Use **vectorized NumPy ops** → avoid Python loops.
- Check **shapes** (`.shape`, `.ndim`) before applying operations.
- Use **broadcasting** instead of manual loops for efficiency.
- Use `dtype=np.float32` in ML/DL for memory efficiency.
- For large matrices, prefer **`@` operator** or `np.matmul` instead of slow nested loops.
- Use **ufuncs** (e.g., `np.exp`) instead of `math.exp` for arrays.

---
