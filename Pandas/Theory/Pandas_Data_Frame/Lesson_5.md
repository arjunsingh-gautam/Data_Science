

# <span style="color:yellow">📌 **Editing / Updating / Deleting / Adding Records in Pandas DataFrame**</span>

We can modify a DataFrame in different ways:

---

# 🔹 1. **Updating Values**

## ✅ Methods

1. **Direct assignment with `.loc[]` or `.iloc[]`**

```python
import pandas as pd

df = pd.DataFrame({
    "name": ["A", "B", "C"],
    "age": [20, 25, 30],
    "marks": [85, 40, 70]
})

# Update specific cell
df.loc[1, "marks"] = 60
df.iloc[2, 1] = 32   # row 2, col 1

# Update entire column
df["age"] = df["age"] + 1

# Update multiple rows
df.loc[df["marks"] < 60, "marks"] = 50
```

✅ **Use Case:** When you want to modify single or multiple records.
⚠️ **Precaution:** Always use `.loc` or `.iloc` for clarity (instead of `df[col][row]` which may cause `SettingWithCopyWarning`).

---

# 🔹 2. **Adding Records**

## ✅ Methods

1. **Adding a New Column**

```python
df["grade"] = ["A", "B", "C"]
```

2. **Insert Column at Specific Position**

```python
df.insert(1, "city", ["Delhi", "Mumbai", "Pune"])
```

3. **Assign Default Value**

```python
df["status"] = "Pass"
```

4. **Appending a New Row (deprecated but works)**

```python
df.loc[3] = ["D", 28, 90, "A", "Chennai", "Pass"]
```

5. **Using `pd.concat()` (Preferred)**

```python
new_row = pd.DataFrame([["E", 26, 75, "B", "Bangalore", "Pass"]],
                       columns=df.columns)
df = pd.concat([df, new_row], ignore_index=True)
```

✅ **Use Case:** Add new feature/record dynamically.
⚠️ **Precaution:** Prefer `concat` over `append` (append is deprecated).

---

# 🔹 3. **Deleting Records**

## ✅ Methods

1. **Drop Column**

```python
df = df.drop("city", axis=1)
```

2. **Drop Multiple Columns**

```python
df = df.drop(["status", "grade"], axis=1)
```

3. **Drop Row by Index**

```python
df = df.drop(2, axis=0)   # drops row with index=2
```

4. **Drop Rows by Condition**

```python
df = df.drop(df[df["marks"] < 60].index)
```

5. **Drop NaN Rows or Columns**

```python
df = df.dropna(axis=0)   # drop rows with NaN
df = df.dropna(axis=1)   # drop columns with NaN
```

✅ **Use Case:** Data cleaning, removing irrelevant rows/columns.
⚠️ **Precaution:** Always set `inplace=True` only if you don’t need original data.

---

# 🔹 4. **Replacing Values**

## ✅ Methods

1. **Single Value Replace**

```python
df["marks"].replace(50, 55, inplace=True)
```

2. **Multiple Values Replace**

```python
df.replace({"marks": {85: 95, 70: 80}}, inplace=True)
```

3. **Replace NaN**

```python
df.fillna(0, inplace=True)
```

✅ **Use Case:** Data standardization, correcting errors.
⚠️ **Precaution:** Use dictionaries for column-specific replacement.

---

# 🔹 5. **Renaming**

```python
df.rename(columns={"name": "student_name"}, inplace=True)
```

✅ **Use Case:** Clean up column names for readability.

---

# 📊 **Summary Table**

| Operation   | Methods Used                         | Example                            | Best Practice                             |
| ----------- | ------------------------------------ | ---------------------------------- | ----------------------------------------- |
| **Update**  | `.loc[]`, `.iloc[]`, assignment      | `df.loc[1,"marks"]=60`             | Use `.loc` / `.iloc` to avoid warnings    |
| **Add**     | New column, `.insert()`, `.concat()` | `df["grade"] = ["A","B","C"]`      | Use `concat` for rows (append deprecated) |
| **Delete**  | `.drop()`, `.dropna()`               | `df.drop("col", axis=1)`           | Don’t forget `axis` (0=row,1=col)         |
| **Replace** | `.replace()`, `.fillna()`            | `df["marks"].replace(40,50)`       | Use dict for multiple replacements        |
| **Rename**  | `.rename()`                          | `df.rename(columns={"old":"new"})` | Use `inplace=False` unless necessary      |

---

# ✅ Best Practices

* ✅ Use `.loc[]` and `.iloc[]` instead of chained indexing (`df['col'][i]`).
* ✅ Keep a copy (`df.copy()`) before major modifications.
* ✅ Prefer **vectorized operations** (`df['col']+10`) instead of loops.
* ✅ Use `.drop()` carefully (by default returns new DataFrame).
* ✅ Avoid `inplace=True` unless memory optimization is critical.

---

