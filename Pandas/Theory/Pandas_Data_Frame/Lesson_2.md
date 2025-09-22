
#  <span style="color:yellow">📌 **DataFrame Attributes in Pandas**</span>

---

## 🔹 1. **Commonly Used Attributes**

| Attribute    | What it Stores                  | Use Case                       | Example                              |
| ------------ | ------------------------------- | ------------------------------ | ------------------------------------ |
| `df.shape`   | Tuple → (rows, cols)            | Know dataset size              | `df.shape → (100, 5)`                |
| `df.columns` | Index of column labels          | Get or set column names        | `df.columns → Index(['A','B'])`      |
| `df.index`   | Index of row labels             | Get or set row labels          | `df.index → RangeIndex(0, 100)`      |
| `df.dtypes`  | Data type of each column        | Check column datatypes         | `df.dtypes → int64, float64, object` |
| `df.values`  | Numpy array of data             | Extract raw data for NumPy ops | `df.values`                          |
| `df.ndim`    | Number of dimensions            | Confirm it’s 2D                | `df.ndim → 2`                        |
| `df.size`    | Total number of elements        | Quick element count            | `df.size → rows × cols`              |
| `df.empty`   | Boolean → True if no data       | Check if DataFrame is empty    | `df.empty → False`                   |
| `df.axes`    | List of row + col index objects | For iteration                  | `[df.index, df.columns]`             |

---

## 🔹 2. **Extended Attributes**

| Attribute  | What it Stores                               | Use Case                    | Example                          |
| ---------- | -------------------------------------------- | --------------------------- | -------------------------------- |
| `df.T`     | Transpose (swap rows & cols)                 | Switch orientation          | `df.T`                           |
| `df.at`    | Accessor for **label-based** scalar access   | Fast single-value access    | `df.at[0,'A']`                   |
| `df.iat`   | Accessor for **integer-based** scalar access | Fast single-value access    | `df.iat[0,1]`                    |
| `df.loc`   | Label-based indexing                         | Slice rows/cols by label    | `df.loc[0:2,'A':'B']`            |
| `df.iloc`  | Position-based indexing                      | Slice rows/cols by position | `df.iloc[0:2,0:2]`               |
| `df.style` | Styler object                                | Pretty HTML representation  | `df.style.background_gradient()` |

---

## 🔹 3. **Special Attributes**

| Attribute           | What it Stores                    | Use Case                              |
| ------------------- | --------------------------------- | ------------------------------------- |
| `df.isna()`         | Boolean DataFrame → NaN detection | Missing value analysis                |
| `df.notna()`        | Opposite of `isna()`              | Valid data check                      |
| `df.memory_usage()` | Memory usage per column           | Optimize performance                  |
| `df.describe()`     | Statistical summary               | Quick EDA (Exploratory Data Analysis) |

---

## 🔹 4. **Examples**

```python
import pandas as pd

data = {
    'Name': ['Alice', 'Bob', 'Charlie'],
    'Age': [25, 30, 35],
    'City': ['Delhi', 'Mumbai', 'Bangalore']
}
df = pd.DataFrame(data)

print("Shape:", df.shape)       # (3,3)
print("Columns:", df.columns)   # Index(['Name','Age','City'])
print("Index:", df.index)       # RangeIndex(start=0, stop=3)
print("Dtypes:\n", df.dtypes)   # object, int64, object
print("Values:\n", df.values)   # Raw NumPy array
print("Size:", df.size)         # 9
print("Empty?:", df.empty)      # False
print("Axes:", df.axes)         # [RangeIndex(0,3), Index([...])]
print("Transpose:\n", df.T)     # Swap rows and cols
```

---

## 🔹 5. **Most Important Attributes for Daily Use**

* `shape` → Know dataset dimensions.
* `columns` → Access or rename columns.
* `dtypes` → Check/convert datatypes before analysis.
* `head()` / `tail()` (technically methods, but often used like attributes).
* `index` → Useful for row labels, merging, and slicing.
* `empty` → Check if DataFrame has no data.
* `memory_usage()` → Optimize performance on large datasets.

---

# ✅ **In short**

* **Attributes** tell you about the DataFrame’s **structure and metadata** (not operations).
* The **core ones** (`shape`, `columns`, `index`, `dtypes`, `values`) are used in almost every analysis.
* Use them for **quick inspection, validation, and debugging**.

---

Great question 🙌 — this confusion is very common. Let’s clear it step by step.

---

# 📌 How `df.duplicated()` Works

👉 By default, **`df.duplicated()` checks for duplicate rows (entire row tuples)** — i.e., it compares all column values in a row against the previous ones.

---

## 🔹 1. Default Behavior (`df.duplicated()`)

* Each row is treated as a **tuple of all column values**.
* If an **entire row (all columns)** matches a **previous row**, it is marked `True` (duplicate).
* Only **the first occurrence** is considered `False` (unique), later ones are `True`.

**Example:**

```python
import pandas as pd

df = pd.DataFrame({
    'A': [1, 2, 2, 3, 1],
    'B': ['x', 'y', 'y', 'z', 'x']
})

print(df)
print(df.duplicated())
```

**Output:**

```
   A  B
0  1  x
1  2  y
2  2  y
3  3  z
4  1  x

0    False
1    False
2     True   # same as row 1 (2,y)
3    False
4     True   # same as row 0 (1,x)
dtype: bool
```

👉 Here rows `(2, y)` and `(1, x)` are **duplicates of entire rows**, not just columns separately.

---

## 🔹 2. Checking Duplicates on Specific Columns

You can restrict duplicate detection to **certain columns** using `subset=`.

```python
df.duplicated(subset=['A'])
```

Checks duplicates only in column `A`.

---

## 🔹 3. Controlling Which Duplicate to Keep

The `keep` parameter decides which duplicate is marked as `False` (unique) vs `True` (duplicate).

* `keep='first'` → First occurrence is kept, others marked duplicate (default).
* `keep='last'` → Last occurrence kept, earlier ones marked duplicate.
* `keep=False` → All duplicates marked as `True`.

```python
df.duplicated(keep='last')
df.duplicated(keep=False)
```

---

## 🔹 4. Relation to `drop_duplicates()`

* `df.duplicated()` → Returns Boolean mask.
* `df.drop_duplicates()` → Actually removes duplicate rows.

---

# ✅ **Answer to Your Question**

* `df.duplicated()` checks **entire rows as tuples of all column values by default**.
* It does **not** check individual elements independently.
* You can change the behavior using `subset` (specific columns).

---

