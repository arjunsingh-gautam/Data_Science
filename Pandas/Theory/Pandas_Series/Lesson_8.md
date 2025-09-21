# <span style="color:rebeccapurple">**Important Series Methods**</span>



# **1. `astype()` – Change the data type of Series**

**Syntax:**

```python
Series.astype(dtype, copy=True, errors='raise')
```

**Attributes:**

* `dtype` → target data type (`int`, `float`, `str`, etc.)
* `copy` → whether to return a new Series or modify (default True)
* `errors` → `'raise'` (default) or `'ignore'` if conversion fails

**Use:** Convert Series data type safely.

**Example:**

```python
import pandas as pd

s = pd.Series([1,2,3])
s_float = s.astype(float)
print(s_float)
```

**Use Case:** Convert integer scores to float for calculations, or strings to numeric for analysis.

**Best Practices:**
✅ Use explicit `dtype`
✅ Beware of NaNs; converting to `int` fails if NaN exists

---

# **2. `between()` – Check if values are in a range**

**Syntax:**

```python
Series.between(left, right, inclusive='both')
```

**Attributes:**

* `left`, `right` → range boundaries
* `inclusive` → 'both', 'neither', 'left', 'right'

**Use:** Return a boolean Series indicating if values lie within the range.

**Example:**

```python
s = pd.Series([10, 20, 30, 40])
print(s.between(15, 35))
```

Output:

```
0    False
1     True
2     True
3    False
dtype: bool
```

**Use Case:** Filter Series for values within a specific range (e.g., scores between 50–80)

**Best Practices:**
✅ Use in conditional filtering: `s[s.between(50,80)]`

---

# **3. `clip()` – Limit values within bounds**

**Syntax:**

```python
Series.clip(lower=None, upper=None, inplace=False)
```

**Attributes:**

* `lower` → minimum value
* `upper` → maximum value
* `inplace` → modify original Series

**Use:** Restrict values to a certain range.

**Example:**

```python
s = pd.Series([10, 20, 30, 40])
s_clipped = s.clip(lower=15, upper=35)
print(s_clipped)
```

Output:

```
0    15
1    20
2    30
3    35
dtype: int64
```

**Use Case:** Cap extreme values (outliers) in data preprocessing.

**Best Practices:**
✅ Prefer `.clip()` over manual loops for performance

---

# **4. `drop_duplicates()` – Remove duplicate values**

**Syntax:**

```python
Series.drop_duplicates(keep='first', inplace=False)
```

**Attributes:**

* `keep` → 'first', 'last', False (which to keep)
* `inplace` → modify Series in place

**Use:** Remove repeated values from a Series.

**Example:**

```python
s = pd.Series([1,2,2,3,3,3])
s_unique = s.drop_duplicates()
print(s_unique)
```

Output:

```
0    1
1    2
3    3
dtype: int64
```

**Use Case:** Clean categorical data, e.g., unique product names.

**Best Practices:**
✅ Use `inplace=True` only if you don’t need the original

---

# **5. `isnull()` – Detect missing values**

**Syntax:**

```python
Series.isnull()
```

**Use:** Returns boolean Series; `True` where value is `NaN`.

**Example:**

```python
s = pd.Series([1, None, 3])
print(s.isnull())
```

**Use Case:** Identify missing data before cleaning.

**Best Practices:**
✅ Combine with `.sum()` to count missing values: `s.isnull().sum()`

---

# **6. `dropna()` – Remove missing values**

**Syntax:**

```python
Series.dropna(inplace=False)
```

**Use:** Remove `NaN` values.

**Example:**

```python
s = pd.Series([1, None, 3])
print(s.dropna())
```

**Use Case:** Preprocessing datasets for calculations.

**Best Practices:**
✅ Avoid inplace=True unless necessary, to keep original Series intact

---

# **7. `fillna()` – Fill missing values**

**Syntax:**

```python
Series.fillna(value=None, method=None, inplace=False)
```

**Attributes:**

* `value` → replace NaN with scalar or dict
* `method` → 'ffill' (forward), 'bfill' (backward)
* `inplace` → modify original

**Example:**

```python
s = pd.Series([1, None, 3])
print(s.fillna(0))
```

**Use Case:** Replace missing values with default or computed values for analysis.

**Best Practices:**
✅ Choose method wisely: forward-fill for time series

---

# **8. `isin()` – Check membership in a list**

**Syntax:**

```python
Series.isin(values)
```

**Use:** Returns boolean Series indicating if each element is in `values`.

**Example:**

```python
s = pd.Series([10,20,30,40])
print(s.isin([20,40]))
```

**Use Case:** Filter Series based on allowed categories.

**Best Practices:**
✅ Use for categorical filters instead of `apply(lambda x: x in ...)`

---

# **9. `apply()` – Apply a function element-wise**

**Syntax:**

```python
Series.apply(func)
```

**Use:** Apply custom or Python functions to each element.

**Example:**

```python
s = pd.Series([1,2,3])
print(s.apply(lambda x: x**2))
```

Output:

```
0    1
1    4
2    9
dtype: int64
```

**Use Case:** Complex transformations, e.g., mapping grades or normalizing values.

**Best Practices:**
✅ Prefer **vectorized operations** when possible for speed

---

# **10. `copy()` – Create a deep copy of Series**

**Syntax:**

```python
s_copy = Series.copy(deep=True)
```

**Use:** Prevent modifying the original Series when performing edits.

**Example:**

```python
s = pd.Series([1,2,3])
s2 = s.copy()
s2[0] = 10
print(s)   # original unchanged
```

**Use Case:** Preserve original dataset before transformations.

**Best Practices:**
✅ Always use `.copy()` when passing Series to functions that may modify it

---

# 🔹 **Summary Table**

| Function            | Purpose                     | Example Use Case                   |
| ------------------- | --------------------------- | ---------------------------------- |
| `astype()`          | Convert dtype               | Int → float for calculations       |
| `between()`         | Check values in range       | Filter scores between 50–80        |
| `clip()`            | Limit values within bounds  | Cap outliers                       |
| `drop_duplicates()` | Remove duplicate values     | Clean categorical data             |
| `isnull()`          | Detect missing values       | Count or locate NaNs               |
| `dropna()`          | Remove NaNs                 | Preprocess before analysis         |
| `fillna()`          | Fill missing values         | Replace NaN with default or method |
| `isin()`            | Check membership            | Filter allowed categories          |
| `apply()`           | Apply function element-wise | Transform or normalize values      |
| `copy()`            | Deep copy of Series         | Preserve original before edits     |

---


