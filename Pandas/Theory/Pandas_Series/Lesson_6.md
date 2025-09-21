# <span style="color:rebeccapurple">**Series with Python Functionalities**</span>

## 1. Series as **Dictionary-like**

* Keys = index
* Values = data

```python
import pandas as pd

marks = pd.Series({'maths': 67, 'english': 57, 'science': 89})

# Dictionary-like access
print(marks['maths'])         # 67
print('science' in marks)     # True
print(marks.get('english'))   # 57
```

✅ Use case → When working with **named data** (e.g., marks by subject, sales by region).

---

## 2. Series as **Array-like**

* Behaves like NumPy array.

```python
print(marks[0])       # 67  (positional access)
print(marks.values)   # [67 57 89] (NumPy array)
print(marks.index)    # Index(['maths', 'english', 'science'], dtype='object')
```

✅ Use case → Apply NumPy operations easily.

---

## 3. Series with **Python Built-ins**

Since Series supports iteration and behaves like a container:

```python
print(len(marks))          # 3
print(list(marks))         # [67, 57, 89]
print(sorted(marks))       # [57, 67, 89]
print(sum(marks))          # 213
```

✅ Use case → Quick summaries without extra Pandas methods.

---

## 4. Series with **Python Functions (`map`, `filter`)**

### `map()` → apply function elementwise

```python
print(marks.map(lambda x: x + 5))
```

Output:

```
maths      72
english    62
science    94
dtype: int64
```

### `filter()` → select elements

```python
print(marks[marks > 60])
```

Output:

```
maths      67
science    89
dtype: int64
```

---

## 5. Series with **NumPy Universal Functions (ufuncs)**

```python
import numpy as np

print(np.sqrt(marks))
print(np.mean(marks))
```

✅ Use case → Directly plug Series into mathematical workflows.

---

## 6. Series in **Membership & Iteration**

```python
for subject, score in marks.items():
    print(subject, score)
```

Output:

```
maths 67
english 57
science 89
```

---

## 7. Series with **Python Operators**

* Element-wise arithmetic

```python
print(marks + 10)
```

* Series + Series (aligned by index!)

```python
extra = pd.Series({'maths': 5, 'science': 10, 'english': 3})
print(marks + extra)
```

👉 Unlike lists/arrays, Pandas aligns by **index labels**.

---

## 8. Best Practices

✅ Treat Series as both **dict** (labels) and **array** (values).
✅ Use **NumPy functions** instead of Python loops for speed.
✅ Prefer **vectorized operations** (`marks + 10`) over `map()` when possible.
✅ Use `items()` when you need Pythonic iteration.

---

## 9. Precautions

⚠️ Don’t confuse **label-based** vs **position-based** indexing (`marks['maths']` vs `marks[0]`).
⚠️ Python list-like negative indexing (`marks[-1]`) can be ambiguous → use `.iloc[-1]`.
⚠️ If Series has `NaN`, Python built-ins like `sum()` may behave differently vs Pandas `.sum()`.

---

## 10. Quick Summary Table

| Python Concept  | Series Behavior | Example                    |
| --------------- | --------------- | -------------------------- |
| Dictionary-like | Key = index     | `marks['maths'] → 67`      |
| Array-like      | Position-based  | `marks[0] → 67`            |
| Built-ins       | Works directly  | `sum(marks) → 213`         |
| Iteration       | Label + value   | `for i in marks: ...`      |
| Membership      | Check labels    | `'maths' in marks`         |
| map/filter      | Apply functions | `marks.map(lambda x: x*2)` |
| NumPy functions | Fast ops        | `np.sqrt(marks)`           |
| Arithmetic ops  | Element-wise    | `marks + 10`               |

---

✅ **In short:**
A Series combines the best of **dictionaries, lists, and NumPy arrays**, while keeping label alignment as its superpower.

---

