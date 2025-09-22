

# <span style="color:yellow"> 📌 **Filtering in Pandas DataFrame**</span>

👉 **Filtering = selecting specific rows/columns based on conditions, masks, or labels.**
Pandas provides multiple ways to filter.

---

# 🔹 1. Boolean Indexing (Most Common Filtering)

### ✅ How it works

* Create a **boolean mask** (`True`/`False`) using conditions.
* Apply it inside `df[mask]`.

### Example:

```python
import pandas as pd

df = pd.DataFrame({
    'name': ['A', 'B', 'C', 'D'],
    'age': [20, 25, 30, 35],
    'marks': [85, 40, 70, 90]
})

# Filter rows where marks > 60
filtered = df[df['marks'] > 60]
print(filtered)
```

**Output:**

```
  name  age  marks
0    A   20     85
2    C   30     70
3    D   35     90
```

✅ **Use Case:** Quick row selection with conditions.
⚠️ Best practice → Wrap multiple conditions in parentheses.

```python
df[(df['marks'] > 60) & (df['age'] < 30)]
```

---

# 🔹 2. `isin()` Filtering

### ✅ How it works

* Filters rows where column values are in a given list/set.

### Example:

```python
df[df['name'].isin(['A','C'])]
```

**Output:**

```
  name  age  marks
0    A   20     85
2    C   30     70
```

✅ **Use Case:** Filtering categorical columns with multiple allowed values.

---

# 🔹 3. `between()` Filtering

### ✅ How it works

* Select values between two bounds (inclusive by default).

### Example:

```python
df[df['age'].between(20,30)]
```

**Output:**

```
  name  age  marks
0    A   20     85
1    B   25     40
2    C   30     70
```

✅ **Use Case:** Range-based filtering (e.g., ages 20–30).

---

# 🔹 4. `query()` Method

### ✅ How it works

* Write filtering conditions as a **string expression**.
* Cleaner syntax for complex conditions.

### Example:

```python
df.query("marks > 60 and age < 30")
```

**Output:**

```
  name  age  marks
0    A   20     85
```

✅ **Use Case:** Readable SQL-like queries.
⚠️ Best practice → Avoid when performance is critical (parsing string overhead).

---

# 🔹 5. `loc[]` Filtering

### ✅ How it works

* Use `.loc` with boolean masks for filtering rows + selecting columns.

### Example:

```python
df.loc[df['marks'] > 60, ['name','marks']]
```

**Output:**

```
  name  marks
0    A     85
2    C     70
3    D     90
```

✅ **Use Case:** Filter rows and pick specific columns simultaneously.

---

# 🔹 6. `iloc[]` Filtering

* `.iloc` works with integer positions, so not direct filtering, but you can filter after getting positions.

### Example:

```python
mask = df['marks'] > 60
df.iloc[mask.values]   # convert boolean Series to array
```

✅ **Use Case:** Rare — usually `.loc` is better for filtering.

---

# 🔹 7. `filter()` Method

### ✅ How it works

* Select rows/columns by **labels, regex, or substring**.
* Works differently: not condition-based but **label-based filtering**.

### Example:

```python
# Filter columns
df.filter(items=['name','marks'], axis=1)

# Filter columns starting with 'a'
df.filter(regex='^a', axis=1)
```

✅ **Use Case:** Column selection when you don’t know exact names.

---

# 🔹 8. `mask()` and `where()` for Conditional Filtering

### ✅ How it works

* `where(condition)` → keeps values where condition is True, replaces others with NaN.
* `mask(condition)` → opposite → replaces True with NaN.

### Example:

```python
df.where(df['marks'] > 60)

df.mask(df['marks'] > 60)
```

✅ **Use Case:** Preserve DataFrame shape (useful in pipelines, replacing instead of dropping).

---

# 🔹 9. Filtering Null Values

### ✅ How it works

* Use `.isnull()`, `.notnull()` for filtering missing values.

### Example:

```python
df[df['marks'].notnull()]   # keep rows without NaN
df[df['marks'].isnull()]    # keep rows with NaN
```

✅ **Use Case:** Data cleaning.

---

# 📊 **Comparison Table**

| Technique        | Works On      | Example                           | Use Case                     |
| ---------------- | ------------- | --------------------------------- | ---------------------------- |
| Boolean Indexing | Conditions    | `df[df['marks']>60]`              | Most common row filtering    |
| `isin()`         | Categories    | `df[df['name'].isin(['A','C'])]`  | Filtering by set/list        |
| `between()`      | Numeric range | `df[df['age'].between(20,30)]`    | Range filtering              |
| `query()`        | Expression    | `df.query("marks>60 and age<30")` | SQL-like syntax              |
| `.loc[]`         | Label+mask    | `df.loc[df['marks']>60,['name']]` | Filter + column selection    |
| `.filter()`      | Labels/Regex  | `df.filter(regex='^a', axis=1)`   | Column filtering             |
| `where()`        | Condition     | `df.where(df['marks']>60)`        | Keep shape, replace with NaN |
| `mask()`         | Condition     | `df.mask(df['marks']>60)`         | Opposite of where            |
| `isnull()`       | Missing data  | `df[df['marks'].isnull()]`        | Null filtering               |

---

# ✅ Best Practices

* Use **boolean indexing** for straightforward row filtering.
* Use **`.loc`** when you want filtering + column selection.
* Use **`.isin`** for categorical filtering.
* Use **`.query`** when readability matters (SQL-like).
* Use **`.where`** if you want to preserve shape and avoid dropping rows.
* For performance: avoid chaining too many filters → combine masks with `&` or `|`.

---


