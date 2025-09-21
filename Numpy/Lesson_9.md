# <span style="color:darkcyan">**Important Numpy Methods**</span>

## **np.sort()**
## 1. **Syntax**

```python
numpy.sort(a, axis=-1, kind=None, order=None)
```

### Parameters:

* **`a`** → array-like input (list, tuple, ndarray, etc.).
* **`axis`** (default = `-1`) → axis along which to sort:

  * `-1` = sort along the last axis.
  * `0` = sort column-wise (down rows).
  * `1` = sort row-wise (across columns).
  * `None` = sort the flattened array.
* **`kind`** → sorting algorithm:

  * `'quicksort'` (default) → fast but not stable.
  * `'mergesort'` → stable (preserves order of equal elements).
  * `'heapsort'` → slower, guaranteed O(n log n).
  * `'stable'` → alias for `'mergesort'`.
* **`order`** → for **structured arrays** → specify which field(s) to sort by.

---

## 2. **Examples**

### (a) Sort 1D array

```python
import numpy as np
arr = np.array([3, 1, 5, 2, 4])
print(np.sort(arr))      # [1 2 3 4 5]
```

### (b) Sort 2D array row-wise (default `axis=-1`)

```python
arr = np.array([[3, 1, 2],
                [9, 8, 7]])
print(np.sort(arr))
# [[1 2 3]
#  [7 8 9]]
```

### (c) Sort column-wise (`axis=0`)

```python
print(np.sort(arr, axis=0))
# [[3 1 2]
#  [9 8 7]]
```

### (d) Flatten and sort (`axis=None`)

```python
print(np.sort(arr, axis=None))
# [1 2 3 7 8 9]
```

### (e) Using different algorithms

```python
arr = np.array([5, 2, 2, 1, 3])
print(np.sort(arr, kind='quicksort'))  # Fastest, not stable
print(np.sort(arr, kind='mergesort'))  # Stable
```

### (f) Structured array sorting

```python
dt = np.dtype([('name', 'U10'), ('age', int)])
data = np.array([('Alice', 25), ('Bob', 30), ('Charlie', 20)], dtype=dt)

print(np.sort(data, order='age'))
# [('Charlie', 20) ('Alice', 25) ('Bob', 30)]
```

---

## 3. **Precautions**

1. **Does not sort in place** → returns a new array.

   * Use `arr.sort()` (method) to sort **in place**.
2. **axis confusion** →

   * `axis=0` = sort **column-wise**.
   * `axis=1` = sort **row-wise**.
   * Always double-check!
3. **Sorting changes only that axis** → other dimensions remain in order.
4. **For large arrays** → choose the right algorithm (`mergesort` if stable sorting needed).
5. Sorting modifies **views** too → if you sort a view, original array can change.

---

## 4. **Best Practices**

✅ Use `np.sort(arr, axis=None)` if you just want all elements sorted, ignoring shape.
✅ Use `arr.sort()` if you need **in-place sorting** (saves memory).
✅ Use `kind='stable'` (`mergesort`) if the **relative order of equal elements matters**.
✅ For **structured arrays**, always specify `order='field_name'`.
✅ Explicitly set `axis` when working with 2D/3D arrays to avoid mistakes.

---

## 5. **Quick Recap**

* `np.sort()` → returns a **sorted copy**.
* `arr.sort()` → sorts **in-place**.
* `axis` defines the direction of sorting.
* `kind` controls sorting algorithm.
* `order` sorts structured arrays by field.

---


# 🔹 1. `np.append()`

### ✅ **Syntax**

```python
numpy.append(arr, values, axis=None)
```

* **`arr`** → input array.
* **`values`** → values to append. Must be **broadcastable** with the shape of `arr` (if `axis` is specified).
* **`axis`**:

  * `None` (default) → flattens `arr` before appending.
  * If specified → append along that axis.

---

### ✅ **Examples**

#### (a) Append to 1D array

```python
import numpy as np
arr = np.array([1, 2, 3])
print(np.append(arr, [4, 5]))
# [1 2 3 4 5]
```

#### (b) Append to 2D array along rows (`axis=0`)

```python
arr = np.array([[1, 2], [3, 4]])
print(np.append(arr, [[5, 6]], axis=0))
# [[1 2]
#  [3 4]
#  [5 6]]
```

#### (c) Append to 2D array along columns (`axis=1`)

```python
print(np.append(arr, [[5], [6]], axis=1))
# [[1 2 5]
#  [3 4 6]]
```

---

### ⚠️ **Precautions**

* If `axis=None`, input is **flattened first**:

  ```python
  np.append([[1,2],[3,4]], [5,6])
  # [1 2 3 4 5 6]
  ```
* `np.append()` **does not modify in-place**; it creates a **new array** (slow for large arrays).
* For efficiency, prefer **`np.concatenate`** if you’re repeatedly appending.
* Appended values must match shape of existing dimensions (if `axis` is specified).

---

### 🌟 **Best Practices**

* Use `np.append()` for **quick one-time additions**.
* For multiple appends → collect values in a list and use `np.concatenate()` once (faster).
* Always explicitly specify `axis` when working with >1D arrays.

---

# 🔹 2. `np.expand_dims()`

### ✅ **Syntax**

```python
numpy.expand_dims(arr, axis)
```

* **`arr`** → input array.
* **`axis`** → position of the new axis (can be negative, like `-1` for last).

👉 Purpose: Add a **new dimension** → turns scalars into vectors, vectors into matrices, etc.

---

### ✅ **Examples**

#### (a) Add a new axis to 1D array

```python
arr = np.array([1, 2, 3])
print(arr.shape)                # (3,)

res = np.expand_dims(arr, axis=0)
print(res.shape)                # (1,3)

res = np.expand_dims(arr, axis=1)
print(res.shape)                # (3,1)
```

#### (b) Add axis to 2D array

```python
arr = np.array([[1, 2], [3, 4]])
print(arr.shape)                 # (2,2)

res = np.expand_dims(arr, axis=0)
print(res.shape)                 # (1,2,2)

res = np.expand_dims(arr, axis=-1)
print(res.shape)                 # (2,2,1)
```

---

### ⚠️ **Precautions**

* `axis` must be within the range `[-arr.ndim-1, arr.ndim]`.
  Example: a `(3,)` array (1D) allows `axis=0` or `axis=1`, but not `axis=2`.
* Don’t confuse with **`np.reshape`**:

  * `np.expand_dims` → *inserts* dimension of size 1.
  * `np.reshape` → *rearranges* shape completely.

---

### 🌟 **Best Practices**

* Use `np.expand_dims` when preparing data for ML/DL models (e.g., converting `(H,W)` image → `(H,W,1)` or `(1,H,W)` batch).
* Can be replaced with **`arr[np.newaxis, :]`** or **`arr[:, np.newaxis]`** → more Pythonic and concise.

  ```python
  arr = np.array([1,2,3])
  print(arr[np.newaxis, :].shape)   # (1,3)
  print(arr[:, np.newaxis].shape)   # (3,1)
  ```
* Always think carefully about which axis to expand → it changes broadcasting behavior.

---

# 🔹 Quick Comparison

| Function           | Purpose                                | Modifies array? | Common Use Case                  |
| ------------------ | -------------------------------------- | --------------- | -------------------------------- |
| `np.append()`      | Add new values (flatten or along axis) | ❌ New array     | Extending data                   |
| `np.expand_dims()` | Add a new axis of size 1               | ❌ New array     | ML input reshaping, broadcasting |

---


## **np.where()**

### 1. **Syntax**

```python
numpy.where(condition, [x, y])
```

* **`condition`** → array-like boolean expression.
* **`x`** → optional, values where condition is `True`.
* **`y`** → optional, values where condition is `False`.

**Returns:**

1. If only `condition` is provided → returns **indices** where condition is `True`.
2. If `x` and `y` are provided → returns array formed by **selecting elements from `x` or `y` based on condition\`**.

---

### 2. **Use Cases & Examples**

---

## **(a) Find indices where condition is True**

```python
import numpy as np

arr = np.array([10, 20, 30, 40, 50])
indices = np.where(arr > 25)
print(indices)      # (array([2, 3, 4]),)
print(arr[indices]) # [30 40 50]
```

✅ Explanation:

* `arr > 25` → `[False, False, True, True, True]`
* `np.where(condition)` → returns **tuple of arrays of indices along each axis**.
* Useful for **filtering, locating, or masking elements**.

---

## **(b) Conditional selection / element-wise replacement**

```python
arr = np.array([1, 2, 3, 4, 5])
res = np.where(arr % 2 == 0, arr*10, arr*100)
print(res)
# [100 20 300 40 500]
```

✅ Explanation:

* If element is even → multiply by 10 (`x`)
* If element is odd → multiply by 100 (`y`)

This is equivalent to a vectorized **if-else**, **without a loop**.

---

## **(c) Replace values in an array**

```python
arr = np.array([10, 20, 30, 40, 50])
arr = np.where(arr > 30, 0, arr)
print(arr)  # [10 20 30 0 0]
```

✅ Explanation:

* All values >30 → replaced by 0.
* Others remain unchanged.

---

## **(d) Working with 2D arrays**

```python
arr = np.array([[1, 2, 3], [4, 5, 6]])
indices = np.where(arr > 3)
print(indices)  # (array([1,1,1]), array([0,1,2]))
print(arr[indices])  # [4 5 6]
```

* `np.where` returns a **tuple of arrays** → first array = row indices, second = column indices.

✅ Can also use for **conditional assignment**:

```python
arr = np.where(arr % 2 == 0, -1, arr)
print(arr)
# [[ 1 -1  3]
#  [-1  5 -1]]
```

---

## **(e) Combining with logical conditions**

```python
arr = np.array([10, 20, 30, 40, 50])
res = np.where((arr > 15) & (arr < 45), arr+5, arr)
print(res)  # [10 25 35 45 50]
```

✅ Explanation:

* `&` → element-wise AND
* `|` → element-wise OR
* `~` → NOT
* `np.where` handles **vectorized logical conditions**.

---

### 3. **Precautions**

1. **Shape match**: `x` and `y` must be **broadcastable** to the shape of `condition`.

   ```python
   arr = np.array([1,2,3])
   np.where(arr>1, [10,20], [0]) # ❌ Error: shapes don't broadcast
   ```
2. **Boolean arrays**: `condition` must be array-like or scalar boolean.
3. **Indexing tuple**: `np.where(condition)` returns a tuple → remember to unpack or use for indexing: `arr[np.where(condition)]`.
4. **Vectorized replacement**: always prefer `np.where` over Python loops → faster and memory efficient.

---

### 4. **Best Practices**

✅ Use for **vectorized if-else** statements in ML, DL, data preprocessing.
✅ For **finding indices**, use `np.where(condition)` instead of Python loops.
✅ Combine multiple conditions with `&`, `|`, `~`.
✅ Use broadcasting wisely → `x` and `y` should be compatible with condition shape.
✅ If you just want a **mask**, use the boolean condition directly (`arr > 25`) → no need to wrap with `np.where`.

---

💡 **Summary Table:**

| Usage              | Syntax                                      | Output              | Example                               |
| ------------------ | ------------------------------------------- | ------------------- | ------------------------------------- |
| Find indices       | `np.where(condition)`                       | tuple of indices    | `np.where(arr>3)`                     |
| Conditional select | `np.where(condition, x, y)`                 | array of same shape | `np.where(arr%2==0, arr*10, arr*100)` |
| Replace elements   | `arr = np.where(condition, new_value, arr)` | modified array      | `arr = np.where(arr>30, 0, arr)`      |

---

## **np.argmax() and np.argmin()

### 1. **Syntax**

```python
numpy.argmax(a, axis=None, out=None)
numpy.argmin(a, axis=None, out=None)
```

### Parameters:

* **`a`** → input array.
* **`axis`** → axis along which to find the max/min index:

  * `None` (default) → flatten array and return single index.
  * `0` → along columns (for 2D arrays).
  * `1` → along rows.
* **`out`** → optional array to store the output indices.

### Returns:

* Index (or indices) of the **first occurrence** of the maximum/minimum value along the given axis.

---

### 2. **Use Cases & Examples**

---

## **(a) 1D array**

```python
import numpy as np

arr = np.array([10, 30, 20, 50, 40])

max_idx = np.argmax(arr)
min_idx = np.argmin(arr)

print("Max value index:", max_idx)  # 3
print("Min value index:", min_idx)  # 0

print("Max value:", arr[max_idx])   # 50
print("Min value:", arr[min_idx])   # 10
```

✅ Explanation:

* `np.argmax(arr)` → index of **maximum value** = 50 → index 3
* `np.argmin(arr)` → index of **minimum value** = 10 → index 0

---

## **(b) 2D array along an axis**

```python
arr2 = np.array([[1, 5, 2],
                 [8, 3, 6]])

# Along axis=0 (column-wise)
print("argmax axis=0:", np.argmax(arr2, axis=0))  # [1 0 1]
print("argmin axis=0:", np.argmin(arr2, axis=0))  # [0 1 0]

# Along axis=1 (row-wise)
print("argmax axis=1:", np.argmax(arr2, axis=1))  # [1 2]
print("argmin axis=1:", np.argmin(arr2, axis=1))  # [0 1]
```

✅ Explanation:

* `axis=0` → finds max/min **in each column**.
* `axis=1` → finds max/min **in each row**.
* **First occurrence** is returned if multiple elements are equal.

---

## **(c) Flattened index**

```python
arr2 = np.array([[1, 5, 2],
                 [8, 3, 6]])

print("argmax flattened:", np.argmax(arr2))  # 3 (index in flattened array)
print("argmin flattened:", np.argmin(arr2))  # 0
```

* When `axis=None` → array is flattened in **row-major order (C-style)** and index returned relative to flattened array.

---

### 3. **Precautions**

1. **First occurrence only** → If multiple elements have max/min value, only the **first index** is returned.
2. **Flattening** → Default `axis=None` may confuse beginners; always specify axis for multidimensional arrays if you want axis-wise results.
3. **Return type** → integer indices (can use `.item()` if you need Python int).
4. **NaN values** → `np.argmax()` and `np.argmin()` **ignore NaNs**; if array has NaN, the result may be unexpected. Use `np.nanargmax()` / `np.nanargmin()` instead.

---

### 4. **Best Practices**

✅ Specify `axis` for **clarity** in multi-dimensional arrays.
✅ Use `np.nanargmax()` or `np.nanargmin()` if your data may contain `NaN`.
✅ Combine with indexing to **retrieve the actual max/min values**:

```python
arr = np.array([10, 30, 50, 20])
max_val = arr[np.argmax(arr)]
```

✅ Works well in **ML/DL tasks**:

* Find highest probability class → `np.argmax(predictions, axis=1)`
* Find minimum loss → `np.argmin(loss_array)`

---

### 5. **Quick Recap Table**

| Function      | Description                         | Returns      | Example                   |
| ------------- | ----------------------------------- | ------------ | ------------------------- |
| `np.argmax()` | Index of maximum element            | int or array | `np.argmax([1,5,2]) → 1`  |
| `np.argmin()` | Index of minimum element            | int or array | `np.argmin([1,5,2]) → 0`  |
| `axis`        | Axis along which to compute         | int or array | `np.argmax(arr2, axis=1)` |
| `NaN-safe`    | Use `np.nanargmax` / `np.nanargmin` | int or array | Handles NaNs safely       |

---


