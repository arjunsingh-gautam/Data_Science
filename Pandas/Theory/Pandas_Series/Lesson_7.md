# <span style="color:rebeccapurple">**Plot functions in Pandas**</span>
## 1. The Main Function: `.plot()`

* **Signature** (for Series/DataFrame):

```python
Series.plot(kind=None, ax=None, figsize=None, title=None, grid=None, **kwargs)
DataFrame.plot(kind=None, x=None, y=None, ax=None, subplots=False, layout=None, figsize=None, title=None, grid=None, **kwargs)
```

* By default, Pandas uses **Matplotlib**.
* `kind` argument decides the **type of plot**.

---

## 2. Supported Plot Types (via `kind`)

| Kind              | Plot Type               | Works for                          |
| ----------------- | ----------------------- | ---------------------------------- |
| `line` (default)  | Line plot               | Series & DataFrame                 |
| `bar`             | Vertical bar plot       | Both                               |
| `barh`            | Horizontal bar plot     | Both                               |
| `hist`            | Histogram               | Both                               |
| `box`             | Boxplot                 | Both                               |
| `kde` / `density` | Kernel Density Estimate | Both                               |
| `area`            | Area plot               | Both                               |
| `pie`             | Pie chart               | Series only                        |
| `scatter`         | Scatter plot            | DataFrame only (`x`, `y` required) |
| `hexbin`          | Hexbin plot             | DataFrame only (`x`, `y` required) |

---

## 3. Examples with **Series**

```python
import pandas as pd
import matplotlib.pyplot as plt

marks = pd.Series([67, 57, 89, 100], index=['maths', 'english', 'science', 'hindi'])

# Line plot (default)
marks.plot(title="Marks per Subject")
plt.show()

# Bar plot
marks.plot(kind='bar', title="Marks per Subject")
plt.show()

# Pie chart
marks.plot(kind='pie', autopct='%1.1f%%', title="Marks Distribution")
plt.show()
```

---

## 4. Examples with **DataFrame**

```python
import numpy as np

df = pd.DataFrame({
    'maths': [67, 45, 89, 78],
    'english': [57, 76, 54, 67],
    'science': [89, 65, 76, 88]
}, index=['A', 'B', 'C', 'D'])

# Line plot
df.plot(title="Student Marks", figsize=(7,4))
plt.show()

# Bar plot
df.plot(kind='bar', title="Marks Comparison")
plt.show()

# Box plot
df.plot(kind='box', title="Marks Distribution by Subject")
plt.show()

# Scatter plot
df.plot(kind='scatter', x='maths', y='science', title="Maths vs Science")
plt.show()
```

---

## 5. Customization

Because Pandas plotting is built on **Matplotlib**, you can pass **Matplotlib keyword args**:

```python
marks.plot(kind='bar', color=['red','blue','green','orange'], figsize=(6,4))
plt.xlabel("Subjects")
plt.ylabel("Scores")
plt.title("Marks by Subject")
plt.grid(True)
plt.show()
```

---

## 6. Best Practices

✅ Use Pandas `.plot()` for **quick exploration**.
✅ For more control, switch to **Matplotlib** or **Seaborn**.
✅ Use `figsize` for readability.
✅ Use `title`, `xlabel`, `ylabel` for self-explaining plots.
✅ For larger datasets, prefer **Seaborn/Matplotlib** for better aesthetics.

---

## 7. Precautions

⚠️ `scatter` and `hexbin` are **DataFrame-only** (need `x`, `y`).
⚠️ `pie` is **Series-only**.
⚠️ Pandas plots are **basic**; for advanced styling → use **Seaborn**.
⚠️ Make sure to call `plt.show()` when running outside Jupyter (in scripts).

---

## 8. Quick Reference Table

| Object    | Function            | Example                                   |
| --------- | ------------------- | ----------------------------------------- |
| Series    | `s.plot()`          | `marks.plot(kind='bar')`                  |
| DataFrame | `df.plot()`         | `df.plot(kind='line')`                    |
| DataFrame | `df.plot.scatter()` | `df.plot.scatter(x='maths', y='science')` |
| DataFrame | `df.plot.box()`     | `df.plot.box()`                           |
| Series    | `s.plot.pie()`      | `marks.plot.pie()`                        |

---

✅ **In short:**
Pandas plotting is a **fast, high-level API** for visualization using Matplotlib.
Use `.plot(kind='...')` for quick charts → upgrade to Seaborn/Matplotlib when needed.

---

