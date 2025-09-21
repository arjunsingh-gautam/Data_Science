# <span style="color:darkcyan">**Numpy Array Attributes**</span>

## **Common `ndarray` Attributes**

Suppose:

```python
import numpy as np
arr = np.array([[1, 2, 3], [4, 5, 6]], dtype=np.float32)
```

---

## 1. **`.ndim` → Number of dimensions**

- **Syntax**:

  ```python
  arr.ndim
  ```

- **Use case**: Know whether the data is scalar (0D), vector (1D), matrix (2D), tensor (3D+).
- **Best practice**: Always check before reshaping/feeding into ML models.
- **Example**:

  ```python
  print(arr.ndim)  # 2
  ```

---

## 2. **`.shape` → Dimensions (tuple of sizes)**

- **Syntax**:

  ```python
  arr.shape
  ```

- **Use case**: Essential in DL (batch size, channels, height, width).
- **Best practice**: Prefer `arr.shape[0]` for dataset size instead of hardcoding.
- **Example**:

  ```python
  print(arr.shape)   # (2, 3)
  ```

---

## 3. **`.size` → Total number of elements**

- **Syntax**:

  ```python
  arr.size
  ```

- **Use case**: Confirm reshaping validity (`new_shape` must equal `arr.size`).
- **Best practice**: Use `arr.size` instead of multiplying shape manually.
- **Example**:

  ```python
  print(arr.size)   # 6
  ```

---

## 4. **`.dtype` → Data type of elements**

- **Syntax**:

  ```python
  arr.dtype
  ```

- **Use case**: Needed for memory optimization & ML frameworks (`float32` vs `float64`).
- **Precaution**: Be explicit when precision matters (`float64` for scientific computing, `float32` for DL).
- **Example**:

  ```python
  print(arr.dtype)   # float32
  ```

---

## 5. **`.itemsize` → Bytes per element**

- **Syntax**:

  ```python
  arr.itemsize
  ```

- **Use case**: Memory profiling (e.g., `float32=4 bytes`, `float64=8 bytes`).
- **Example**:

  ```python
  print(arr.itemsize)  # 4
  ```

---

## 6. **`.nbytes` → Total memory (bytes)**

- **Syntax**:

  ```python
  arr.nbytes
  ```

- **Use case**: Large dataset handling, GPU memory management.
- **Example**:

  ```python
  print(arr.nbytes)   # 24 (6 elements × 4 bytes)
  ```

---

## 7. **`.T` → Transpose**

- **Syntax**:

  ```python
  arr.T
  ```

- **Use case**: Switching rows ↔ columns in linear algebra.
- **Precaution**: `.T` only swaps axes (2D matrix transpose). For higher dims use `.transpose()`.
- **Example**:

  ```python
  print(arr.T)
  # [[1. 4.]
  #  [2. 5.]
  #  [3. 6.]]
  ```

---

## 8. **`.real` and `.imag` → Real & Imaginary parts**

- **Syntax**:

  ```python
  arr.real
  arr.imag
  ```

- **Use case**: Complex number arrays (signal processing, quantum computing).
- **Example**:

  ```python
  c = np.array([1+2j, 3+4j])
  print(c.real)  # [1. 3.]
  print(c.imag)  # [2. 4.]
  ```

---

## 9. **`.flat` → Flat iterator**

- **Syntax**:

  ```python
  arr.flat
  ```

- **Use case**: Iterate through elements regardless of shape.
- **Example**:

  ```python
  for x in arr.flat:
      print(x)
  ```

---

## 10. **`.data` → Memory buffer**

- **Syntax**:

  ```python
  arr.data
  ```

- **Use case**: Low-level access (rare in ML, more for C extensions).
- **Precaution**: Don’t manipulate directly unless you know buffer protocols.
- **Example**:

  ```python
  print(arr.data)   # <memory at 0x...>
  ```

---

## **Summary Table**

| Attribute  | Purpose              | Example (for `arr = np.array([[1,2,3],[4,5,6]])`) |
| ---------- | -------------------- | ------------------------------------------------- |
| `ndim`     | Dimensions           | `2`                                               |
| `shape`    | Size along each axis | `(2,3)`                                           |
| `size`     | Total elements       | `6`                                               |
| `dtype`    | Data type            | `int64` (default)                                 |
| `itemsize` | Bytes per element    | `8`                                               |
| `nbytes`   | Total memory         | `48`                                              |
| `T`        | Transpose            | `[[1 4] [2 5] [3 6]]`                             |
| `real`     | Real part            | `[1 2 3] ...`                                     |
| `imag`     | Imaginary part       | `[0 0 0] ...`                                     |
| `flat`     | Flat iterator        | Iterates 1,2,3,4,5,6                              |
| `data`     | Buffer               | `<memory at ...>`                                 |

---

## **Best Practices & Precautions**

1. **Always check `.shape` before reshaping or feeding into ML models.**
   (Avoid shape mismatch errors).

2. **Use `dtype=np.float32` for ML/DL** to save GPU memory.

3. **Monitor `.nbytes` when handling large datasets** (OOM crashes are common in DL).

4. **Use `.T` for quick transpose, but `.transpose()` for multi-dimensional control.**

5. **Never manipulate `.data` directly** unless doing advanced low-level work.

---


