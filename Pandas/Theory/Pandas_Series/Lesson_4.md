# <span style="color:rebeccapurple">**Indexing and Slicing**</span>

## 1. Types of Indexing in Series

A Pandas Series supports **three ways** of accessing data:

1. **Default `[]` indexing**

   * First checks **labels** (index values).
   * If labels are not integers → allows positional access.
   * If labels are integers → negative/positive values are treated as **labels**, not positions.

2. **`.loc[]` → Label-based indexing**

   * Access by **explicit labels** (index values).
   * Supports slicing with labels (inclusive of end).

3. **`.iloc[]` → Position-based indexing**

   * Access by **integer positions** (like Python list).
   * Negative indices work (e.g., `-1` → last element).

---

## 2. Example Series

```python
import pandas as pd

marks = pd.Series(
    [67, 57, 89, 100],
    index=['maths', 'english', 'science', 'hindi'],
    name='Nitish ke Marks'
)
print(marks)
```

Output:

```
maths      67
english    57
science    89
hindi     100
Name: Nitish ke Marks, dtype: int64
```

---

## 3. Indexing Examples

### ✅ Label-based (`[]` or `.loc[]`)

```python
print(marks['maths'])        # 67
print(marks.loc['hindi'])    # 100
```

### ✅ Position-based (`.iloc[]`)

```python
print(marks.iloc[0])         # 67
print(marks.iloc[-1])        # 100
```

### ✅ Default `[]` behavior with string index

```python
print(marks[-1])   # 100 (falls back to position, since index are strings)
```

---

## 4. Slicing in Series

## (a) Label-based slicing (`.loc`)

```python
print(marks.loc['english':'hindi'])
```

Output:

```
english    57
science    89
hindi     100
```

👉 Notice **end is inclusive** (`hindi` included).

---

## (b) Position-based slicing (`.iloc`)

```python
print(marks.iloc[1:3])
```

Output:

```
english    57
science    89
```

👉 Works like Python lists → **end is exclusive** (`3` not included).

---

## (c) Default slicing `[]`

* If **string index** → falls back to **position slicing**.

```python
print(marks[1:3])
```

Output:

```
english    57
science    89
```

* If **integer index** → slicing behaves differently (can mix up label vs position).
  ⚠️ Best to avoid and stick with `.loc[]` / `.iloc[]`.

---

## 5. Best Practices

✅ Use **`.loc[]` for labels**, `.iloc[]` for positions → always explicit.
✅ Avoid ambiguous `s[-1]` — behavior changes based on index type.
✅ Remember:

* **`.loc[]` slicing → inclusive of end.**
* **`.iloc[]` slicing → exclusive of end.**
  ✅ Use `.head()` / `.tail()` for quick look instead of indexing manually.

---

## 6. Precautions

⚠️ If your Series has **integer index values**:

```python
s = pd.Series([10,20,30], index=[0,1,2])
print(s[-1])   # ❌ KeyError (since -1 not in labels)
```

⚠️ If your Series has **string index**:

```python
print(marks[-1])   # ✅ Works (positional fallback)
```

👉 This inconsistency is why `.loc` and `.iloc` are recommended.

---

## 7. Quick Reference Table

| Method              | Type                        | Example                    | End Inclusive? | Notes                             |
| ------------------- | --------------------------- | -------------------------- | -------------- | --------------------------------- |
| `s[label]`          | Label lookup                | `s['maths']`               | N/A            | Ambiguous if labels are integers  |
| `s[pos]`            | Position (if non-int index) | `s[-1]`                    | N/A            | Works only if labels not integers |
| `s.loc[label]`      | Label lookup                | `s.loc['hindi']`           | ✅ Inclusive    | Always use for labels             |
| `s.iloc[pos]`       | Position lookup             | `s.iloc[-1]`               | ❌ Exclusive    | Always use for positions          |
| `s.loc[start:end]`  | Label slice                 | `s.loc['english':'hindi']` | ✅ Inclusive    |                                   |
| `s.iloc[start:end]` | Position slice              | `s.iloc[1:3]`              | ❌ Exclusive    |                                   |

---

✅ **In short:**

* Use `.loc[]` for **labels**
* Use `.iloc[]` for **positions**
* Avoid plain `[]` when index is integers

---



## **Why Negative Indexing in Series is Confusing**

In **Python lists**, negative indexing works naturally:

```python
lst = [10, 20, 30, 40]
print(lst[-1])   # 40
```

But in **Pandas Series**, indexing works differently because **Pandas prioritizes labels (index values)** over positions.

---

## **Two Ways to Index in Series**

1. **Label-based indexing** (`s[]` → tries to match index label first)
2. **Position-based indexing** (`s.iloc[]`)

---

## **Case 1: When index is numeric (like 0,1,2,3...)**

```python
import pandas as pd

s = pd.Series([10, 20, 30, 40])
print(s)
```

Output:

```
0    10
1    20
2    30
3    40
dtype: int64
```

Now:

```python
print(s[-1])   # ❌ Error: -1 not in index
```

👉 Reason: `s[]` first checks if `-1` exists as a **label** in the index. Since your index is `0,1,2,3` → it fails.

✅ Correct way (position-based):

```python
print(s.iloc[-1])   # 40
```

---

## **Case 2: When index contains -1 as a label**

```python
s = pd.Series([10, 20, 30], index=[-1, 0, 1])
print(s[-1])   # ✅ Works → 10
```

👉 Here, `-1` exists in the **index labels**, so Pandas returns the corresponding value.

---

## **Use Cases**

* **`s.loc[label]`** → When you want to fetch by label (including -1 if it’s in index).
* **`s.iloc[position]`** → When you want Python-style position indexing (negative allowed).

---

## **Best Practices**

✅ Always use `.iloc[]` for **position-based indexing** → avoids confusion.
✅ Use `.loc[]` when you want to fetch values by **index label**.
✅ Don’t mix label vs. position in the same code block → maintain clarity.
✅ If you want consistent Python list-like negative indexing → stick with `.iloc`.

---

## **Precautions**

⚠️ `s[-1]` will throw `KeyError` unless `-1` is an actual index label.
⚠️ If your dataset has both numeric labels and positions → always explicitly use `.iloc` or `.loc`.
⚠️ Don’t rely on shorthand `s[]` when working with mixed indexes.

---

✅ **Summary:**

* Negative indexing is **not "disallowed"** in Pandas Series.
* It depends on **whether `-1` exists as a label**.
* For position-based negative indexing, always use `.iloc[-1]`.

---

Excellent observation 👌 You’ve caught one of the **trickiest Pandas behaviors** that often confuses beginners. Let’s break it down carefully.

---

# 🔹 Your Code

```python
import pandas as pd

marks = {
    'maths':67,
    'english':57,
    'science':89,
    'hindi':100
}

marks_series = pd.Series(marks, name='nitish ke marks')
print(marks_series)
```

Output:

```
maths      67
english    57
science    89
hindi     100
Name: nitish ke marks, dtype: int64
```

Now:

```python
print(marks_series[-1])   # ✅ 100
```

---

# 🔹 Why This Works Here?

* The **index** of your Series is **non-numeric labels** (`maths, english, science, hindi`).
* In this case, when you do `marks_series[-1]`, Pandas **falls back to positional indexing** because `-1` is **not found as a label**.
* So it treats `-1` as “last element”, just like a Python list.

👉 Therefore, you get `100`.

---

# 🔹 Why Didn’t It Work in Numeric Index Case?

If your index is `0,1,2,3`:

```python
s = pd.Series([10,20,30,40])
print(s[-1])   # ❌ KeyError
```

* Here Pandas first looks for label `-1` in the index.
* Since index = `[0,1,2,3]`, label `-1` doesn’t exist.
* So you get an error.

---

# 🔹 Rule of Thumb

* If **index is non-integer labels** → `s[-1]` behaves like **position-based indexing**.
* If **index is integer labels** → `s[-1]` is treated as **label lookup**, not position → KeyError.

---

# 🔹 Best Practices

✅ **Always use `.iloc[]` for positions** (safe & consistent):

```python
marks_series.iloc[-1]   # 100
```

✅ **Always use `.loc[]` for labels**:

```python
marks_series.loc['hindi']   # 100
```

⚠️ Avoid plain `s[-1]`, because behavior changes **depending on index type** → leads to bugs in real projects.

---

✅ **Summary:**

* `marks_series[-1]` worked because your index is **strings**, so Pandas fell back to positional indexing.
* With numeric indexes, Pandas will **first try label lookup** and throw error if label doesn’t exist.

---
