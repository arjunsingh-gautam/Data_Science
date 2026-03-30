# <span style="color:yellow">**Quantiles**</span>

## 🧠 **What Does `.quantile()` Do?**

In **Pandas**, the `.quantile()` method returns the value **below which a given fraction (quantile) of the data falls**.

That is:

> `.quantile(q)` → gives the value at the `q`th quantile (where `q` is between 0 and 1).

---

## 🧩 **Syntax**

```python
DataFrame.quantile(q=0.5, axis=0, numeric_only=True, interpolation='linear')
```

### Parameters:

| Parameter       | Description                                                                                                                          |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| `q`             | The quantile(s) to compute (float or list of floats between 0 and 1).                                                                |
| `axis`          | 0 for column-wise (default), 1 for row-wise.                                                                                         |
| `numeric_only`  | Only include numeric columns (True by default).                                                                                      |
| `interpolation` | Defines how to handle when the quantile lies between two data points (`'linear'`, `'nearest'`, `'lower'`, `'higher'`, `'midpoint'`). |

---

## 🧮 **Example 1 — Basic Use on a Series**

```python
import pandas as pd

data = pd.Series([3, 7, 8, 12, 13, 14, 18, 21, 23, 27])

print("Q1 (25th percentile):", data.quantile(0.25))
print("Q2 (50th percentile / median):", data.quantile(0.5))
print("Q3 (75th percentile):", data.quantile(0.75))
```

**Output:**

```
Q1 (25th percentile): 7.75
Q2 (50th percentile / median): 13.5
Q3 (75th percentile): 21.5
```

✅ Same as we computed manually earlier.

---

## 🧮 **Example 2 — Multiple Quantiles**

```python
data.quantile([0.25, 0.5, 0.75])
```

**Output:**

```
0.25     7.75
0.50    13.50
0.75    21.50
dtype: float64
```

---

## 🧮 **Example 3 — On a DataFrame**

```python
import pandas as pd

df = pd.DataFrame({
    'Maths': [88, 92, 79, 93, 85],
    'Physics': [75, 88, 89, 91, 72],
    'Chemistry': [84, 90, 78, 94, 88]
})

print(df.quantile(0.5))  # Median of each subject
```

**Output:**

```
Maths         88.0
Physics       88.0
Chemistry     88.0
Name: 0.5, dtype: float64
```

So `.quantile(0.5)` = median for each column.

---

## 🧮 **Example 4 — Different Interpolation**

If your quantile lies between two points, you can control how it’s calculated.

```python
data = pd.Series([10, 20, 30, 40])

print(data.quantile(0.25, interpolation='linear'))   # 17.5
print(data.quantile(0.25, interpolation='lower'))    # 10
print(data.quantile(0.25, interpolation='higher'))   # 20
print(data.quantile(0.25, interpolation='nearest'))  # 20
print(data.quantile(0.25, interpolation='midpoint')) # 15
```

---

## 🎯 **Real-World Use Cases**

### 1. **Outlier Detection**

You can use quantiles to find **IQR (Interquartile Range)** and detect outliers.

```python
Q1 = df['Physics'].quantile(0.25)
Q3 = df['Physics'].quantile(0.75)
IQR = Q3 - Q1

outliers = df[(df['Physics'] < Q1 - 1.5*IQR) | (df['Physics'] > Q3 + 1.5*IQR)]
print(outliers)
```

👉 Finds rows where Physics marks are unusually low or high.

---

### 2. **Percentile-based Filtering**

Filter top 10% or bottom 10% performers.

```python
threshold = df['Maths'].quantile(0.9)
top_students = df[df['Maths'] >= threshold]
```

---

### 3. **Data Binning / Categorization**

Create bins like “Low”, “Medium”, “High” based on quantiles:

```python
df['Performance'] = pd.qcut(df['Chemistry'], q=3, labels=['Low', 'Medium', 'High'])
print(df)
```

---

### 4. **Feature Engineering in ML**

Quantiles can help in:

- Handling skewed data
- Winsorizing (limiting extreme values)
- Transforming continuous features into categorical ones for models

---

## 🔍 **Summary Table**

| Task                              | Example                       | Result             |
| --------------------------------- | ----------------------------- | ------------------ |
| Compute median                    | `data.quantile(0.5)`          | Middle value       |
| Compute Q1 & Q3                   | `data.quantile([0.25, 0.75])` | Quartiles          |
| Compute quantiles for all columns | `df.quantile(0.5)`            | Medians per column |
| Detect outliers                   | via IQR                       | Filter extremes    |
| Divide into quantile bins         | `pd.qcut(df[col], q=4)`       | Quartile labels    |

---
