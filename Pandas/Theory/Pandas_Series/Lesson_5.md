# <span style="color:rebeccapurple">**Editing Series**</span>
## 1. Updating Existing Values

You can modify values by **label** or **position**:

### By Label (`.loc`)

```python
import pandas as pd

marks = pd.Series([67, 57, 89, 100], index=['maths', 'english', 'science', 'hindi'])

marks.loc['english'] = 60
print(marks)
```

Output:

```
maths      67
english    60   # updated
science    89
hindi     100
dtype: int64
```

---

### By Position (`.iloc`)

```python
marks.iloc[2] = 95   # science
print(marks)
```

Output:

```
maths      67
english    60
science    95   # updated
hindi     100
dtype: int64
```

---

## 2. Updating Multiple Values

### By Label List

```python
marks.loc[['maths', 'science']] = [70, 90]
```

### By Condition

```python
marks[marks > 90] = 99   # replace all >90 with 99
```

---

## 3. Adding New Elements

If you assign a value to a **new index**, Pandas **adds it**:

```python
marks['history'] = 85
print(marks)
```

Output:

```
maths      70
english    60
science    90
hindi      99
history    85   # new element added
dtype: int64
```

---

## 4. Removing Elements

### Using `.drop()`

```python
marks = marks.drop('history')
print(marks)
```

### Using `.pop()`

```python
val = marks.pop('english')
print(val)     # 60
print(marks)   # english removed
```

---

## 5. Renaming Labels

### Single Rename

```python
marks.rename({'maths': 'mathematics'}, inplace=True)
```

### Full Index Rename

```python
marks.index = ['Maths', 'English', 'Science', 'Hindi']
```

---

## 6. Vectorized Updates (Fast)

Instead of looping, Pandas allows **vectorized edits**:

```python
marks = marks + 5     # add 5 to all values
marks = marks * 2     # double all marks
```

---

## 7. Best Practices

✅ Use `.loc[]` for label-based editing → explicit and safe.
✅ Use `.iloc[]` for position-based editing.
✅ Avoid `s[index] = value` when index is integers → can confuse label vs position.
✅ Use **vectorized operations** instead of loops for performance.
✅ When dropping values, use `.drop()` with `inplace=True` if you don’t want to create a new Series.

---

## 8. Precautions

⚠️ If you assign a value to a new label, it will **expand** the Series (sometimes unintended).
⚠️ If dtype is `int` and you insert a `NaN`, dtype will change to `float`.
⚠️ Inplace edits (`inplace=True`) are **irreversible**, use carefully.

---

## 9. Quick Summary Table

| Operation          | Code Example               | Effect                     |
| ------------------ | -------------------------- | -------------------------- |
| Update by label    | `s.loc['a'] = 10`          | Changes value at label `a` |
| Update by position | `s.iloc[0] = 20`           | Changes first element      |
| Update multiple    | `s.loc[['a','b']] = [1,2]` | Updates multiple labels    |
| Conditional update | `s[s>50] = 99`             | Replace all >50 with 99    |
| Add new element    | `s['new'] = 5`             | Adds new index             |
| Drop element       | `s.drop('a')`              | Removes index `a`          |
| Pop element        | `s.pop('b')`               | Removes & returns value    |
| Rename element     | `s.rename({'a':'alpha'})`  | Renames index              |
| Vectorized update  | `s = s+5`                  | Adds 5 to all values       |

---

✅ **In short:**

* Series is **mutable**.
* You can edit by **label (`.loc`)** or **position (`.iloc`)**.
* Assigning to new labels **adds values**, dropping removes them.
* Always use explicit `.loc` / `.iloc` for clarity.

---

