

# 📌 **`rank()` Method in Pandas**

## 🔹 1. What it does

* Assigns **ranks** (1, 2, 3, …) to values in a Series/DataFrame.
* Handles **ties (duplicate values)** according to the chosen method.
* Supports ranking in **ascending/descending order**.

---

## 🔹 2. Syntax

```python
DataFrame.rank(
    axis=0,
    method='average',
    numeric_only=False,
    na_option='keep',
    ascending=True,
    pct=False
)
```

---

## 🔹 3. Parameters & Their Use

| Parameter         | Description                                                                                                                                                                                                                                                            | Example / Use                         |
| ----------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------- |
| **axis**          | 0 → rank row-wise (default, across columns); 1 → rank column-wise                                                                                                                                                                                                      | `df.rank(axis=1)`                     |
| **method**        | How to assign ranks when values tie:<br> - `'average'` → average of ranks (default)<br> - `'min'` → lowest rank assigned<br> - `'max'` → highest rank assigned<br> - `'first'` → assign rank in order of appearance<br> - `'dense'` → like 'min', but no gaps in ranks | `df['col'].rank(method='min')`        |
| **numeric\_only** | Whether to rank only numeric data                                                                                                                                                                                                                                      | Useful when DataFrame has mixed types |
| **na\_option**    | `'keep'` (default, NaN stays NaN), `'top'` (NaN gets smallest rank), `'bottom'` (NaN gets largest rank)                                                                                                                                                                | Handle missing values                 |
| **ascending**     | True → smallest = rank 1; False → largest = rank 1                                                                                                                                                                                                                     | `df['col'].rank(ascending=False)`     |
| **pct**           | True → return ranks as percentage of total group (0–1 scale)                                                                                                                                                                                                           | `df['col'].rank(pct=True)`            |

---

## 🔹 4. Examples

### ✅ Example 1: Basic Ranking

```python
import pandas as pd
import numpy as np

s = pd.Series([100, 200, 100, 300, np.nan])

print(s.rank())
```

**Output (default = average method):**

```
0    1.5   # average of ranks 1 and 2
1    3.0
2    1.5
3    4.0
4    NaN
dtype: float64
```

---

### ✅ Example 2: Different Methods for Ties

```python
print(s.rank(method="min"))
print(s.rank(method="max"))
print(s.rank(method="first"))
print(s.rank(method="dense"))
```

**Output:**

```
min:    [1.0, 3.0, 1.0, 4.0, NaN]
max:    [2.0, 3.0, 2.0, 4.0, NaN]
first:  [1.0, 3.0, 2.0, 4.0, NaN]
dense:  [1.0, 2.0, 1.0, 3.0, NaN]
```

---

### ✅ Example 3: Descending Order

```python
s.rank(ascending=False)
```

Output:

```
0    3.5
1    2.0
2    3.5
3    1.0
4    NaN
```

---

### ✅ Example 4: Percentage Ranks

```python
s.rank(pct=True)
```

Output:

```
0    0.375
1    0.750
2    0.375
3    1.000
4      NaN
```

(Values expressed as fraction of total ranks).

---

### ✅ Example 5: DataFrame Ranking

```python
df = pd.DataFrame({
    "maths": [90, 80, 90],
    "science": [70, 80, 60]
})

df.rank(axis=0)  # rank within each column
df.rank(axis=1)  # rank across columns for each row
```

---

## 🔹 5. Use Cases

* **Sports results** → ranking players based on scores.
* **Data analysis** → normalize values by rank instead of absolute values.
* **Finance** → rank stocks by returns.
* **Machine Learning** → feature engineering (rank-based transformation).

---

## 🔹 6. Best Practices

* ✅ Always specify `method` to control how ties are handled.
* ✅ Use `ascending=False` if higher values mean better rank (e.g., marks).
* ✅ Use `pct=True` when you need percentile-based normalization.
* ✅ Handle `NaN` carefully → default is keep, but you may want `'top'` or `'bottom'`.

---



# 📌 **`set_index()` Method in Pandas**

## 🔹 1. What it does

* Changes the **index (row labels)** of a DataFrame.
* You can set one or more existing columns as the index.
* Makes data lookup and hierarchical indexing easier.

---

## 🔹 2. Syntax

```python
DataFrame.set_index(
    keys,
    drop=True,
    append=False,
    inplace=False,
    verify_integrity=False
)
```

---

## 🔹 3. Parameters Explained

| Parameter             | Description                                                                   | Example                                      |
| --------------------- | ----------------------------------------------------------------------------- | -------------------------------------------- |
| **keys**              | Column label(s) to set as index                                               | `"col1"` or `["col1", "col2"]`               |
| **drop**              | If True (default), remove the column(s) from DataFrame after setting as index | `drop=False` keeps the column                |
| **append**            | If True, append new index column(s) to existing index instead of replacing    | Useful for hierarchical (multi-level) index  |
| **inplace**           | If True, modifies the DataFrame in place                                      | `df.set_index("id", inplace=True)`           |
| **verify\_integrity** | Checks for duplicate index values, raises error if found                      | `df.set_index("col", verify_integrity=True)` |

---

## 🔹 4. Examples

### ✅ Example 1: Basic Usage

```python
import pandas as pd

df = pd.DataFrame({
    "id": [1, 2, 3],
    "name": ["A", "B", "C"],
    "marks": [85, 90, 95]
})

print(df.set_index("id"))
```

**Output:**

```
   name  marks
id             
1     A     85
2     B     90
3     C     95
```

👉 Now `id` is the index.

---

### ✅ Example 2: Keep Column Instead of Dropping

```python
df.set_index("id", drop=False)
```

Output:

```
    id name  marks
id                 
1    1    A     85
2    2    B     90
3    3    C     95
```

👉 `id` is both a column and an index.

---

### ✅ Example 3: Multi-Index (Hierarchical Index)

```python
df.set_index(["id", "name"])
```

Output:

```
        marks
id name       
1  A       85
2  B       90
3  C       95
```

👉 MultiIndex created with `(id, name)`.

---

### ✅ Example 4: Append to Existing Index

```python
df2 = df.set_index("id")
df2.set_index("name", append=True)
```

Output:

```
         marks
id name        
1  A        85
2  B        90
3  C        95
```

👉 Now index = `(id, name)`.

---

### ✅ Example 5: Verify Integrity

```python
df = pd.DataFrame({
    "id": [1, 1, 2],
    "name": ["A", "B", "C"]
})

df.set_index("id", verify_integrity=True)
```

👉 Raises `ValueError` because `id=1` is duplicated.

---

## 🔹 5. Use Cases

* Setting unique identifiers (`id`, `roll_no`, `order_id`) as index.
* Creating **hierarchical indexes** for multi-level grouping (e.g., `year, month`).
* Faster **lookup & slicing** with meaningful row labels.

---

## 🔹 6. Best Practices

* ✅ Use `verify_integrity=True` when the index should be unique (avoids hidden bugs).
* ✅ Keep `drop=False` if you want to keep the column for later analysis.
* ✅ Use MultiIndex when your data has natural hierarchies (e.g., country → city).
* ✅ Reset the index back to default integers when needed:

  ```python
  df.reset_index()
  ```

---



