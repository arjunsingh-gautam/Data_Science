# <span style="color:darkcyan">**Reshape**</span>

## **Syntax**

Two equivalent ways:

```python
numpy.reshape(a, newshape, order='C')
```

or

```python
arr.reshape(newshape, order='C')
```

### Parameters:

- **`a`** → The input array (when using `np.reshape`).
- **`newshape`** → Tuple or int

  - Example: `(2,3)` → 2 rows, 3 columns.
  - Can use `-1` for **automatic inference** (NumPy figures out the missing dimension).

- **`order`** (default `'C'`) → memory layout:

  - `'C'` → row-major (C-style, rows first).
  - `'F'` → column-major (Fortran-style, columns first).
  - `'A'` → adopt array’s existing memory order.

---

## **Constraints & Limitations**

1. **Total elements must match**

   - `np.reshape` does not change the number of elements.
   - Formula: `np.prod(original_shape) == np.prod(newshape)`

   ```python
   arr = np.arange(6)     # 6 elements
   arr.reshape(2,3)       # OK
   arr.reshape(4,2)       # ❌ Error (8 != 6)
   ```

2. **-1 only once**

   - You can use `-1` in **one dimension only** → NumPy infers the correct value.

   ```python
   arr = np.arange(12)
   arr.reshape(3, -1)   # (3, 4)
   arr.reshape(-1, 6)   # (2, 6)
   arr.reshape(-1, -1)  # ❌ Error
   ```

3. **Does not copy data (most cases)**

   - Returns a **view** of the same data when possible (fast).
   - If memory isn’t contiguous, a copy may be made.

---

## **Behavior**

- **Flattening** (1D reshape):

  ```python
  arr = np.arange(6).reshape(-1)   # [0 1 2 3 4 5]
  ```

- **Multi-dimensional reshape**:

  ```python
  arr = np.arange(12).reshape(3,4)
  # [[ 0  1  2  3]
  #  [ 4  5  6  7]
  #  [ 8  9 10 11]]
  ```

- **Order parameter effect**:

  ```python
  arr = np.arange(6)
  print(arr.reshape(2,3, order='C'))  # row-major
  print(arr.reshape(2,3, order='F'))  # column-major
  ```

Output:

```
[[0 1 2]
 [3 4 5]]

[[0 2 4]
 [1 3 5]]
```

---

## **Use Cases in ML/DL/AI**

1. **Flattening images / tensors**

   ```python
   image = np.random.rand(28,28)       # grayscale image
   vector = image.reshape(-1)          # flatten to (784,)
   ```

2. **Reshaping batches**

   ```python
   data = np.arange(24).reshape(4,6)   # 4 samples, 6 features
   reshaped = data.reshape(2,2,6)      # 2 batches of 2 samples
   ```

3. **Preparing inputs for models**

   - CNN expects `(batch, height, width, channels)`.
   - RNN expects `(timesteps, batch, features)`.

4. **Broadcasting-friendly shapes**

   ```python
   arr = np.arange(6).reshape(2,3)
   bias = np.array([1,2,3])
   print(arr + bias)   # broadcasting works
   ```

---

## **Examples**

### ✅ Valid reshape

```python
arr = np.arange(8)
reshaped = arr.reshape(2,4)
print(reshaped)
```

Output:

```
[[0 1 2 3]
 [4 5 6 7]]
```

### ❌ Invalid reshape

```python
arr.reshape(3,3)   # Error (8 elements → cannot reshape into 9)
```

### ✅ Using `-1` (auto-infer)

```python
arr = np.arange(12)
print(arr.reshape(3,-1))   # (3,4)
print(arr.reshape(-1,2,2)) # (3,2,2)
```

---

## **Summary**

- `reshape` **changes the view** of the data, not the data itself.
- **Constraint**: Total number of elements must remain the same.
- `-1` lets NumPy infer the missing dimension (only once).
- **Use cases**: flattening, preparing ML/DL tensors, batching, reshaping for broadcasting.
- `order='C'` (row-major) vs `order='F'` (column-major) controls element order in reshaping.

---
