# <span style="color:darkcyan">**Indexing and Slicing in Numpy**</span>


# 🔹 1. Indexing in NumPy

Indexing means **picking out elements from an array**. NumPy supports several ways:

---

## (a) **Basic Indexing**

Like Python lists, but works with **multi-dimensional arrays**.

✅ Example:

```python
import numpy as np
arr = np.array([[10, 20, 30], 
                [40, 50, 60]])

print(arr[0, 0])  # First row, first col → 10
print(arr[1, 2])  # Second row, third col → 60
```

---

## (b) **Negative Indexing**

Count from the end.

```python
print(arr[-1, -1])  # Last element → 60
print(arr[-2, -3])  # First element (10)
```

---

## (c) **Boolean Indexing**

Select elements using conditions.

```python
arr = np.array([1, 2, 3, 4, 5, 6])
print(arr[arr > 3])   # Elements greater than 3 → [4 5 6]
```

---

## (d) **Fancy Indexing**

Pick elements at multiple positions using lists/arrays.

```python
arr = np.array([10, 20, 30, 40, 50])
print(arr[[0, 2, 4]])  # → [10 30 50]
```

Works in 2D too:

```python
arr = np.array([[1, 2], [3, 4], [5, 6]])
print(arr[[0, 2], [1, 0]])  # → [2, 5]
```

👉 Explanation: Picks (0,1) and (2,0).

---

# 🔹 2. Slicing in NumPy

Slicing extracts **subarrays** instead of single elements.
**General syntax:**

```python
arr[start:stop:step]
```

* `start`: starting index (default = 0)
* `stop`: stop before this index (default = length)
* `step`: step size (default = 1)

---

## (a) 1D Slicing

```python
arr = np.arange(10)  # [0 1 2 3 4 5 6 7 8 9]
print(arr[2:7])      # [2 3 4 5 6]
print(arr[:5])       # [0 1 2 3 4]
print(arr[::2])      # [0 2 4 6 8]
print(arr[::-1])     # Reverse → [9 8 7 6 5 4 3 2 1 0]
```

---

## (b) 2D Slicing

```python
arr = np.array([[1, 2, 3], 
                [4, 5, 6], 
                [7, 8, 9]])

print(arr[0:2, 1:3])   # Rows 0-1, Cols 1-2 → [[2 3] [5 6]]
print(arr[:, 0])       # All rows, first col → [1 4 7]
print(arr[1, :])       # Second row → [4 5 6]
print(arr[:, ::2])     # All rows, step 2 in cols → [[1 3] [4 6] [7 9]]
```

---

## (c) Higher Dimensions

```python
arr = np.arange(24).reshape(2, 3, 4)
# Shape = (2 blocks, 3 rows, 4 cols)

print(arr[0, :, :])   # First block → 2D array
print(arr[:, 1, :])   # All blocks, 2nd row
print(arr[:, :, 2])   # All blocks, 3rd column
```

---

# 🔹 3. Important Behavior

* **Slicing gives a *view*, not a copy**
  (changes affect the original array).

```python
arr = np.arange(10)
sub = arr[2:5]
sub[:] = 99
print(arr)  # [ 0  1 99 99 99  5  6  7  8  9]
```

👉 To avoid this: use `.copy()`

```python
sub = arr[2:5].copy()
```

---

# 🔹 4. Use Cases

* Extracting **submatrices** (useful in ML, image processing).
* **Filtering** data with conditions (boolean indexing).
* **Vectorized batch operations** (fancy indexing).
* **Data preprocessing** (e.g., splitting features and labels).
* **Efficient reverse/stride** operations without loops.

---

# 🔹 5. Best Practices & Precautions

✅ Use slicing instead of Python loops → it’s **faster**.
✅ Always check `.shape` after slicing.
⚠️ Remember: slicing is usually a **view**, so modifying the slice changes the original. Use `.copy()` if you need independence.
✅ Prefer **boolean indexing** for filtering conditions instead of writing loops.

---


## 1. Simultaneous Slicing (`arr[::, ::, :]`)

* **Syntax**: `arr[start:stop:step, start:stop:step, start:stop:step]`
* You give slicing instructions for **all axes at once** inside one `[]`.
* This is evaluated **in one shot** → NumPy applies all slices together, producing a **view** of the original array.

✅ Example:

```python
import numpy as np
arr = np.arange(27).reshape(3,3,3)

print("Original array shape:", arr.shape)

# Simultaneous slicing
res = arr[::, ::, :]
print(res.shape)
```

👉 Here, `arr[::, ::, :]` means:

* `::` (take all rows) along axis 0
* `::` (take all columns) along axis 1
* `:` (take all depth elements) along axis 2

Result → `res` is a view of shape `(3,3,3)` (same as original).

---

## 2. Sequential Slicing (`arr[:][:]`)

* **First** NumPy applies the first `[:]`.
* That gives you a new array object (often still a view).
* Then it applies the **second slice** (`[:]`) to the result.

⚠️ The big difference: each slicing is applied **step by step**, not on all axes together.
This can cause confusion, especially in 2D+ arrays.

✅ Example:

```python
arr = np.arange(9).reshape(3,3)
print("Original arr:\n", arr)

res1 = arr[:, ::-1]     # simultaneous slice (reverse cols)
res2 = arr[:][::-1]     # sequential slice
print("\nSimultaneous slice arr[:, ::-1]:\n", res1)
print("\nSequential slice arr[:][::-1]:\n", res2)
```

👉 Dry-run:

* `arr[:, ::-1]`:

  * Take all rows (`:`)
  * Reverse columns (`::-1`)
    ✅ Output = array with **columns reversed**.

* `arr[:][::-1]`:

  * First `arr[:]` → takes **all rows**, result is just a copy of `arr`.
  * Then `[::-1]` → applied along the **first axis of this copy**, so it reverses **rows**.
    ❌ Different meaning than above!

---

## 3. Why this difference?

* `arr[a, b]` = true **multi-axis slicing**.
* `arr[a][b]` = first slice → returns a temporary array, then slice that array → effectively **nested indexing**.

Think of `arr[:, ::-1]` as "tell me exactly what you want in both directions at once".
But `arr[:][::-1]` as "give me everything first, then I’ll slice again".

---

## 4. Rule of Thumb

* Always use **simultaneous slicing** (`arr[axis1, axis2, axis3]`).
* Avoid sequential slicing (`arr[:][:]`) unless you really mean nested operations.
* Sequential slicing is slower (extra intermediate object) and often **not what you intend**.

---

## 5. Higher-Dim Example

```python
arr = np.arange(24).reshape(2,3,4)
print("Shape:", arr.shape)

# Simultaneous: take first 2 rows, last 2 cols across all depth
sim = arr[:2, :, -2:]
print("Simultaneous shape:", sim.shape)

# Sequential: arr[:2][:, -2:]
seq = arr[:2][:, -2:]
print("Sequential shape:", seq.shape)
```

👉 Difference:

* `arr[:2, :, -2:]` → slice all 3 axes at once → shape `(2,3,2)`.
* `arr[:2]` → shape `(2,3,4)`; then `[:, -2:]` → keep last 2 columns of axis 1 → shape `(2,2,4)`.
  ⚠️ Different result!

---

✅ **Best Practice**: Always slice in **one set of brackets** → `arr[axis0_slice, axis1_slice, axis2_slice]`.

---


