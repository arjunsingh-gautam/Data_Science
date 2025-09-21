# <span style="color:darkcyan">**Numpy ways to change data-type**</span>

## **Ways to Change Data Type**

## 1. **Using `.astype()` (recommended)**

```python
new_arr = arr.astype(new_dtype)
```

- Returns a **new array** with the specified data type.
- Original array remains unchanged.

---

## 2. **Using `dtype` at creation**

```python
arr = np.array([1, 2, 3], dtype=np.float32)
```

- Directly creates array with desired type.

---

## 3. **Using `np.asarray()` with dtype**

```python
arr = np.asarray([1, 2, 3], dtype=np.complex64)
```

---

## 4. **Using `np.astype()` at function level**

(not common, `.astype()` is preferred)

---

## **Use Cases**

1. **Memory optimization**

   - Use `float32` instead of `float64` in ML/DL → halves memory usage.

2. **Precision control**

   - Use `float64` for scientific computing to avoid rounding errors.

3. **Data conversion**

   - Convert `str` → `int`, `float` → `int`, etc.

4. **Compatibility with frameworks**

   - Many ML frameworks (TensorFlow, PyTorch) expect `float32`.

---

## **Precautions & Best Practices**

- ✅ **Prefer `.astype()`** → safe and explicit.
- ⚠️ **Beware of data loss**:

  - `float → int` truncates decimal part.
  - `complex → real` discards imaginary part.

- ✅ Always **check `.dtype`** after conversion.
- ⚠️ **Do not use in-place casting** (`arr = arr.astype(...)`) when large arrays are involved, unless needed — it duplicates memory.

---

## **Examples**

### 1. Integer → Float

```python
import numpy as np

arr = np.array([1, 2, 3, 4])
new_arr = arr.astype(np.float32)

print(arr, arr.dtype)       # [1 2 3 4] int64
print(new_arr, new_arr.dtype) # [1. 2. 3. 4.] float32
```

---

### 2. Float → Integer (⚠️ decimal truncated)

```python
arr = np.array([1.7, 2.9, 3.3])
new_arr = arr.astype(int)

print(new_arr)   # [1 2 3]
```

---

### 3. Integer → Boolean

```python
arr = np.array([0, 1, 2, 0])
new_arr = arr.astype(bool)

print(new_arr)   # [False  True  True  False]
```

---

### 4. Complex → Real (⚠️ imaginary part lost)

```python
arr = np.array([1+2j, 3+4j])
new_arr = arr.astype(float)

print(new_arr)   # [1. 3.]
```

---

### 5. Memory Saving in DL

```python
arr = np.arange(1e6, dtype=np.float64)
print("Before:", arr.nbytes / 1e6, "MB")

arr32 = arr.astype(np.float32)
print("After:", arr32.nbytes / 1e6, "MB")
```

Output:

```
Before: 8.0 MB
After: 4.0 MB
```

---

## **Summary**

- **Syntax**: `arr.astype(new_dtype)` (preferred).
- **Use cases**: memory optimization, framework compatibility, type conversion.
- **Best practice**: always check `.dtype`, avoid unwanted truncation.
- **Precaution**: converting to `int` or `float` may lose data.

---
