# <span style="color:darkcyan">**Reshaping and Stacking**</span>



## 1. What is Concatenation?

In NumPy, **concatenation** means **joining arrays together along an existing axis** (not creating a new axis).

👉 Function:

```python
np.concatenate((arr1, arr2, ...), axis=0, out=None, dtype=None, casting="same_kind")
```

* `arr1, arr2,...` → sequence of arrays.
* `axis` → the dimension along which arrays are joined.
* `out` → optional array to store result.
* `dtype` → change data type if needed.

---

## 2. Rules of Concatenation

✅ **Rule 1**: Arrays must have the **same shape** in all dimensions **except the one along which you concatenate**.

✅ **Rule 2**: The `axis` you choose **expands**, while others must be **equal**.

❌ If shapes don’t match → `ValueError`.

---

## 3. Axis Values & Their Meaning

* **axis=0** → concatenate along rows (vertical stacking).
* **axis=1** → concatenate along columns (horizontal stacking).
* **axis=2** → for 3D arrays → concatenate along depth (stacking along 3rd dimension).

👉 If `axis=None` → arrays are flattened before joining.

---

## 4. Examples

### ✅ Example 1: 1D Arrays

```python
import numpy as np
a = np.array([1,2,3])
b = np.array([4,5,6])

print(np.concatenate((a,b), axis=0))
```

Output:

```
[1 2 3 4 5 6]
```

👉 Only `axis=0` works for 1D arrays.

---

### ✅ Example 2: 2D Arrays with `axis=0` (row-wise)

```python
a = np.array([[1,2],
              [3,4]])
b = np.array([[5,6],
              [7,8]])

print(np.concatenate((a,b), axis=0))
```

Output:

```
[[1 2]
 [3 4]
 [5 6]
 [7 8]]
```

👉 Rows increased (4 instead of 2), columns same.

---

### ✅ Example 3: 2D Arrays with `axis=1` (column-wise)

```python
print(np.concatenate((a,b), axis=1))
```

Output:

```
[[1 2 5 6]
 [3 4 7 8]]
```

👉 Columns increased (4 instead of 2), rows same.

---

### ✅ Example 4: 3D Arrays (axis=0,1,2)

```python
x = np.arange(8).reshape(2,2,2)
y = np.arange(8,16).reshape(2,2,2)

print("Shape along axis=0:", np.concatenate((x,y), axis=0).shape)
print("Shape along axis=1:", np.concatenate((x,y), axis=1).shape)
print("Shape along axis=2:", np.concatenate((x,y), axis=2).shape)
```

Output:

```
Shape along axis=0: (4, 2, 2)   # more "blocks"
Shape along axis=1: (2, 4, 2)   # more rows
Shape along axis=2: (2, 2, 4)   # more columns
```

---

### ✅ Example 5: `axis=None` (flatten and join)

```python
a = np.array([[1,2],[3,4]])
b = np.array([[5,6]])
print(np.concatenate((a,b), axis=None))
```

Output:

```
[1 2 3 4 5 6]
```

---

## 5. Limitations & Precautions

⚠️ **Dimension mismatch not allowed** → all dimensions except the concatenation axis must match.

```python
a = np.array([[1,2]])
b = np.array([[3,4,5]])
np.concatenate((a,b), axis=0)   # ❌ Error (different column count)
```

⚠️ For **higher dimensional arrays** → always check shape using `.shape` before concatenation.

⚠️ If you want to **add a new axis** (instead of merging existing ones), use `np.stack()` instead of `concatenate`.

---

## 6. Use Cases

* **Row/Column appending** to datasets.
* **Batching** data for ML models.
* **Merging images/signals** along specific dimensions.
* **Data preprocessing** when combining multiple sources.

---

✅ **Summary:**

* `np.concatenate()` joins arrays along an existing axis.
* `axis=0` → stack vertically (rows).
* `axis=1` → stack horizontally (columns).
* `axis=2` → stack depth-wise (3D arrays).
* Constraint → all other dimensions must match.

---



## 1. `np.hstack()` → **Horizontal stacking**

* Stacks arrays **side by side (columns)**.
* Equivalent to `np.concatenate(arrs, axis=1)` for 2D arrays.
* For 1D arrays → concatenates into a single 1D array.

### ✅ Syntax:

```python
np.hstack(tup)
```

### ✅ Example 1: 1D arrays

```python
import numpy as np
a = np.array([1,2,3])
b = np.array([4,5,6])

print(np.hstack((a,b)))
```

Output:

```
[1 2 3 4 5 6]
```

### ✅ Example 2: 2D arrays

```python
a = np.array([[1,2],[3,4]])
b = np.array([[5,6],[7,8]])

print(np.hstack((a,b)))
```

Output:

```
[[1 2 5 6]
 [3 4 7 8]]
```

👉 Works like `axis=1` concatenation.
⚠️ Rule: Row count must match.

---

## 2. `np.vstack()` → **Vertical stacking**

* Stacks arrays **on top of each other (rows)**.
* Equivalent to `np.concatenate(arrs, axis=0)` for 2D arrays.
* For 1D arrays → stacks them as new rows.

### ✅ Syntax:

```python
np.vstack(tup)
```

### ✅ Example 1: 1D arrays

```python
a = np.array([1,2,3])
b = np.array([4,5,6])

print(np.vstack((a,b)))
```

Output:

```
[[1 2 3]
 [4 5 6]]
```

### ✅ Example 2: 2D arrays

```python
a = np.array([[1,2],[3,4]])
b = np.array([[5,6],[7,8]])

print(np.vstack((a,b)))
```

Output:

```
[[1 2]
 [3 4]
 [5 6]
 [7 8]]
```

👉 Works like `axis=0` concatenation.
⚠️ Rule: Column count must match.

---

## 3. `np.stack()` → **Stack along a new axis**

* Unlike `concatenate`, `stack` **creates a new dimension**.
* You choose which axis to insert along.

### ✅ Syntax:

```python
np.stack(arrays, axis=0)
```

### ✅ Example 1: 1D arrays

```python
a = np.array([1,2,3])
b = np.array([4,5,6])

print(np.stack((a,b), axis=0))  # stack as rows
print(np.stack((a,b), axis=1))  # stack as columns
```

Output:

```
[[1 2 3]       [[1 4]
 [4 5 6]]  vs   [2 5]
                [3 6]]
```

👉 Notice: Shape changed from `(3,)` to `(2,3)` or `(3,2)`.

---

### ✅ Example 2: 2D arrays

```python
a = np.array([[1,2],[3,4]])
b = np.array([[5,6],[7,8]])

print(np.stack((a,b), axis=0))  # new "block" dimension
print(np.stack((a,b), axis=1))  # new "row" dimension
print(np.stack((a,b), axis=2))  # new "col" dimension
```

Output:

```
axis=0: shape (2,2,2)
[[[1 2]   [[5 6]
  [3 4]],  [7 8]]]

axis=1: shape (2,2,2)
[[[1 2]   [[5 6]]
  [3 4]],  [7 8]]]

axis=2: shape (2,2,2)
[[[1 5]   [[2 6]]
  [3 7]],  [4 8]]]
```

👉 Key: A **new axis** is introduced.

---

## 4. Limitations & Constraints

### `hstack`:

* Works like `axis=1`.
* ❌ Requires same row count in 2D.

### `vstack`:

* Works like `axis=0`.
* ❌ Requires same column count in 2D.

### `stack`:

* Requires arrays of **exact same shape**.
* Adds a new dimension → output shape grows by 1.

---

## 5. Use Cases

* `hstack` → combine **features** side by side (e.g., merging feature sets in ML).
* `vstack` → combine **datasets** row-wise (e.g., stacking training + test data).
* `stack` → create **batches** of data (ML, DL).

  * Example: stacking multiple images into a batch: `(height, width, channels)` → `(batch, height, width, channels)`.

---

✅ **Summary Table**

| Function      | Axis Effect   | Adds New Axis? | Constraint                           |
| ------------- | ------------- | -------------- | ------------------------------------ |
| `concatenate` | Existing axis | ❌ No           | Shapes must match except concat axis |
| `hstack`      | Axis=1 (cols) | ❌ No           | Same rows                            |
| `vstack`      | Axis=0 (rows) | ❌ No           | Same cols                            |
| `stack`       | New axis      | ✅ Yes          | All shapes must match                |

---





# 🧩 1. What is `np.split()`?

Imagine you have a **big chocolate bar (array)**, and you want to **break it into smaller pieces**.
That’s exactly what `np.split()` does — it **splits one array into many sub-arrays**.

---

## 2. Syntax

```python
np.split(ary, indices_or_sections, axis=0)
```

* **`ary`** → the big chocolate bar (your array).
* **`indices_or_sections`** → how you want to cut it:

  * If it’s an **integer `n`** → cut the array into `n` equal parts.
  * If it’s a **list of indices** → cut at those positions.
* **`axis`** → direction of the cut:

  * `axis=0` → cut along rows (top-to-bottom).
  * `axis=1` → cut along columns (left-to-right).

---

## 3. How it works

👉 Think of `axis` as telling **which way to hold the knife**:

* `axis=0`: hold knife horizontally, cut across rows.
* `axis=1`: hold knife vertically, cut across columns.

---

## 4. Examples

### ✅ Example 1: Split 1D array equally

```python
import numpy as np
a = np.array([1,2,3,4,5,6])
print(np.split(a, 3))
```

Output:

```
[array([1, 2]), array([3, 4]), array([5, 6])]
```

👉 Big array cut into **3 equal sub-arrays**.

⚠️ Rule: Length must be divisible by `n` (here 6 ÷ 3 = 2).

---

### ✅ Example 2: Split 1D array by indices

```python
a = np.array([1,2,3,4,5,6])
print(np.split(a, [2,4]))
```

Output:

```
[array([1, 2]), array([3, 4]), array([5, 6])]
```

👉 First cut at index `2`, then at index `4`.
Like slicing bread at different places.

---

### ✅ Example 3: Split 2D array along rows (`axis=0`)

```python
a = np.array([[1,2],
              [3,4],
              [5,6],
              [7,8]])

print(np.split(a, 2, axis=0))
```

Output:

```
[array([[1, 2],
        [3, 4]]),
 array([[5, 6],
        [7, 8]])]
```

👉 Cut **horizontally** into 2 row blocks.

---

### ✅ Example 4: Split 2D array along columns (`axis=1`)

```python
print(np.split(a, 2, axis=1))
```

Output:

```
[array([[1],
        [3],
        [5],
        [7]]),
 array([[2],
        [4],
        [6],
        [8]])]
```

👉 Cut **vertically** into 2 column blocks.

---

## 5. Rules & Precautions

1. If you use an **integer `n`**, the array’s size along that axis must be divisible by `n`.

   ```python
   a = np.array([1,2,3,4,5])
   np.split(a, 3)   # ❌ Error (5 not divisible by 3)
   ```
2. Using **indices list** is more flexible because it doesn’t require equal splits.

---

## 6. Summary (Child-like Explanation 🧒)

* `np.split` is like **cutting a big chocolate bar** into smaller pieces.
* `axis=0` → cut **horizontally** (rows).
* `axis=1` → cut **vertically** (columns).
* You can say:

  * “Cut into `n` equal parts” (integer).
  * “Cut at these spots” (list of indices).

---



## 1. `np.hsplit` (Horizontal Split)

* **Meaning:** Split an array **horizontally**, i.e. **along columns** → same as `np.split(..., axis=1)`.
* **Syntax:**

  ```python
  np.hsplit(array, sections)
  ```

  * `array`: the NumPy array to split.
  * `sections`: integer (number of equal parts) or list of indices where to split.

✅ Example:

```python
import numpy as np

a = np.arange(16).reshape(4, 4)
print(a)

# Split into 2 equal parts (left vs right)
print(np.hsplit(a, 2))

# Split at specific column index
print(np.hsplit(a, [1, 3]))
```

Output:

```
[[ 0  1  2  3]
 [ 4  5  6  7]
 [ 8  9 10 11]
 [12 13 14 15]]

[array([[ 0,  1],
       [ 4,  5],
       [ 8,  9],
       [12, 13]]),

 array([[ 2,  3],
       [ 6,  7],
       [10, 11],
       [14, 15]])]

[array([[ 0],
       [ 4],
       [ 8],
       [12]]),

 array([[ 1,  2],
       [ 5,  6],
       [ 9, 10],
       [13, 14]]),

 array([[ 3],
       [ 7],
       [11],
       [15]])]
```

👉 **Use case:** cutting dataset into **features (X)** and **labels (y)**, or separating left/right halves.

---

## 2. `np.vsplit` (Vertical Split)

* **Meaning:** Split an array **vertically**, i.e. **along rows** → same as `np.split(..., axis=0)`.
* **Syntax:**

  ```python
  np.vsplit(array, sections)
  ```

✅ Example:

```python
a = np.arange(16).reshape(4, 4)
print(np.vsplit(a, 2))       # Split into 2 parts (top vs bottom)
print(np.vsplit(a, [1, 3]))  # Split at specific row indices
```

Output:

```
[array([[0, 1, 2, 3]]),
 array([[ 4,  5,  6,  7],
        [ 8,  9, 10, 11]]),
 array([[12, 13, 14, 15]])]
```

👉 **Use case:** splitting dataset into **training vs testing rows**, or top/bottom halves.

---

## 3. Key Rules & Limitations

* `hsplit` → cuts **columns** → needs array with at least 2D.
* `vsplit` → cuts **rows** → works fine as long as rows ≥ parts.
* If `sections` is an integer → must divide dimension evenly.
  Example: `np.hsplit(a, 3)` requires number of columns to be divisible by 3.
* If `sections` is a list → indices define split points (more flexible).

---

## 4. Best Practices

* Use **`hsplit` / `vsplit`** for readability (clear intent).
* Use **`split(..., axis=0/1)`** if you want more generality (works on any axis).
* Always check array shape before splitting.

---

👉 In short:

* `hsplit = split(..., axis=1)` → **left/right**.
* `vsplit = split(..., axis=0)` → **top/bottom**.

---


