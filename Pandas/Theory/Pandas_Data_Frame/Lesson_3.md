

# <span style="color:yellow"> 📌 **Pandas DataFrame Methods**</span>

---

## 🔹 1. **Basic Inspection / Overview**

| Method       | Function                               | Syntax          | Usage                      | Best Practice                       |
| ------------ | -------------------------------------- | --------------- | -------------------------- | ----------------------------------- |
| `head()`     | First *n* rows                         | `df.head(n=5)`  | Quick peek at dataset      | Use for debugging & sanity check    |
| `tail()`     | Last *n* rows                          | `df.tail(n=5)`  | End of dataset             | Good for checking appended data     |
| `info()`     | Summary (index, dtypes, nulls, memory) | `df.info()`     | Dataset health check       | Run early after loading data        |
| `describe()` | Stats summary of numeric cols          | `df.describe()` | EDA (mean, std, quartiles) | Use `include='all'` for all dtypes  |
| `shape`      | (rows, cols)                           | `df.shape`      | Size check                 | Always verify after transformations |
| `ndim`       | Dimensions                             | `df.ndim`       | Confirm 2D                 | DataFrames are always 2D            |
| `size`       | Total elements                         | `df.size`       | Count elements             | Rare but useful                     |
| `empty`      | True if empty                          | `df.empty`      | Validation                 | Use before saving/exporting         |

---

## 🔹 2. **Selection & Indexing**

| Method   | Function                          | Syntax          | Usage             | Best Practice          |
| -------- | --------------------------------- | --------------- | ----------------- | ---------------------- |
| `loc[]`  | Label-based selection             | `df.loc[2,'A']` | Row/col by label  | Safer than `[]`        |
| `iloc[]` | Position-based selection          | `df.iloc[2,0]`  | Row/col by index  | Always 0-based         |
| `at[]`   | Fast label-based scalar access    | `df.at[2,'A']`  | Single element    | Faster than `loc`      |
| `iat[]`  | Fast position-based scalar access | `df.iat[2,0]`   | Single element    | Faster than `iloc`     |
| `xs()`   | Cross-section                     | `df.xs(1)`      | Get row/col slice | Useful with MultiIndex |

---

## 🔹 3. **Sorting & Ordering**

| Method          | Function       | Syntax                   | Usage             | Best Practice                     |
| --------------- | -------------- | ------------------------ | ----------------- | --------------------------------- |
| `sort_values()` | Sort by values | `df.sort_values(by='A')` | Rank, ordering    | Use `ascending=False` when needed |
| `sort_index()`  | Sort by index  | `df.sort_index()`        | Reorder rows/cols | Useful after merges               |

---

## 🔹 4. **Summarization & Statistics**

| Method                 | Function           | Syntax        | Usage                | Best Practice                         |
| ---------------------- | ------------------ | ------------- | -------------------- | ------------------------------------- |
| `sum()`                | Column-wise sum    | `df.sum()`    | Totals               | Watch for object dtypes               |
| `mean()`               | Mean               | `df.mean()`   | Average              | Use `numeric_only=True` in new pandas |
| `median()`             | Median             | `df.median()` | Robust stats         | Good for skewed data                  |
| `std()`                | Standard deviation | `df.std()`    | Dispersion           | Use with numeric data                 |
| `var()`                | Variance           | `df.var()`    | Variability          | Good for ML prep                      |
| `min()`, `max()`       | Min/Max values     | `df.min()`    | Bounds               | Combine with `.idxmin()`              |
| `idxmin()`, `idxmax()` | Index of min/max   | `df.idxmin()` | Locate extremes      | Useful in finance/ML                  |
| `count()`              | Non-null count     | `df.count()`  | Data completeness    | Use in missing value analysis         |
| `corr()`               | Correlation        | `df.corr()`   | Feature relation     | Use heatmap for visualization         |
| `cov()`                | Covariance         | `df.cov()`    | Statistical modeling | For advanced stats                    |
| `mode()`               | Most common value  | `df.mode()`   | Categorical analysis | Use for imputation                    |

---

## 🔹 5. **Missing Data Handling**

| Method                | Function             | Syntax         | Usage             | Best Practice            |
| --------------------- | -------------------- | -------------- | ----------------- | ------------------------ |
| `isna()` / `isnull()` | Detect NaNs          | `df.isna()`    | Missing values    | Interchangeable          |
| `notna()`             | Opposite of `isna()` | `df.notna()`   | Filter valid data | Combine with `.sum()`    |
| `dropna()`            | Remove NaN rows/cols | `df.dropna()`  | Data cleaning     | Use `axis=1` for cols    |
| `fillna()`            | Replace NaN          | `df.fillna(0)` | Imputation        | Can use `method='ffill'` |

---

## 🔹 6. **Duplicate Handling**

| Method              | Function                   | Syntax                 | Usage             | Best Practice                    |
| ------------------- | -------------------------- | ---------------------- | ----------------- | -------------------------------- |
| `duplicated()`      | Boolean mask of duplicates | `df.duplicated()`      | Detect duplicates | Use `subset=` for selective cols |
| `drop_duplicates()` | Remove duplicates          | `df.drop_duplicates()` | Data cleaning     | Combine with `keep` parameter    |

---

## 🔹 7. **Transformation & Reshaping**

| Method                  | Function                | Syntax                                          | Usage           | Best Practice               |
| ----------------------- | ----------------------- | ----------------------------------------------- | --------------- | --------------------------- |
| `transpose()` / `T`     | Swap rows/cols          | `df.T`                                          | Pivoting        | Use sparingly on large data |
| `pivot()`               | Reshape (unique values) | `df.pivot(index, columns, values)`              | Wide format     | Requires unique index       |
| `pivot_table()`         | Reshape + agg           | `df.pivot_table(index, values, aggfunc='mean')` | Group summaries | More flexible               |
| `melt()`                | Unpivot                 | `pd.melt(df)`                                   | Long format     | Good for tidy data          |
| `stack()` / `unstack()` | Reshape index levels    | `df.stack()`                                    | MultiIndex ops  | Advanced reshaping          |

---

## 🔹 8. **Merging & Joining**

| Method                    | Function        | Syntax                        | Usage            | Best Practice                 |
| ------------------------- | --------------- | ----------------------------- | ---------------- | ----------------------------- |
| `merge()`                 | SQL-style join  | `pd.merge(df1, df2, on='id')` | Relational joins | Always check `how=`           |
| `join()`                  | Join by index   | `df1.join(df2)`               | Index-based      | Simpler than merge            |
| `concat()`                | Concatenate DFs | `pd.concat([df1, df2])`       | Append/stack     | Use `axis=1` for side-by-side |
| `append()` *(deprecated)* | Append rows     | `df1.append(df2)`             | Add rows         | Use `concat` instead          |

---

## 🔹 9. **String & Category Operations**

| Method               | Function            | Syntax                         | Usage         | Best Practice         |
| -------------------- | ------------------- | ------------------------------ | ------------- | --------------------- |
| `str` accessor       | String ops          | `df['col'].str.lower()`        | Clean text    | Chain methods         |
| `astype('category')` | Convert to category | `df['col'].astype('category')` | Memory saving | Use for repeated text |

---

## 🔹 10. **I/O Operations**

| Method       | Function         | Syntax                     | Usage              | Best Practice           |
| ------------ | ---------------- | -------------------------- | ------------------ | ----------------------- |
| `to_csv()`   | Save as CSV      | `df.to_csv('file.csv')`    | Export             | Use `index=False`       |
| `to_excel()` | Save as Excel    | `df.to_excel('file.xlsx')` | Reports            | Requires `openpyxl`     |
| `to_json()`  | Save as JSON     | `df.to_json('file.json')`  | Web APIs           | Choose `orient` wisely  |
| `to_sql()`   | Save to DB       | `df.to_sql('table', conn)` | DB storage         | Use chunks for big data |
| `to_dict()`  | Convert to dict  | `df.to_dict()`             | Flexible use       | Specify `orient`        |
| `to_numpy()` | Convert to NumPy | `df.to_numpy()`            | ML/scientific work | Better than `.values`   |

---

## 🔹 11. **Index & Column Management**

| Method          | Function                   | Syntax                             | Usage           | Best Practice                  |
| --------------- | -------------------------- | ---------------------------------- | --------------- | ------------------------------ |
| `set_index()`   | Set new index              | `df.set_index('col')`              | Better indexing | Use inplace or assign          |
| `reset_index()` | Reset to default int index | `df.reset_index()`                 | Flatten index   | Useful after groupby           |
| `rename()`      | Rename cols/index          | `df.rename(columns={'old':'new'})` | Clarify names   | Always rename before exporting |
| `reindex()`     | Reorder index              | `df.reindex([0,2,1])`              | Align datasets  | Can fill missing values        |

---

## 🔹 12. **GroupBy & Aggregation**

| Method        | Function            | Syntax                                | Usage               | Best Practice          |
| ------------- | ------------------- | ------------------------------------- | ------------------- | ---------------------- |
| `groupby()`   | Group rows          | `df.groupby('col').mean()`            | Aggregations        | Chain with agg methods |
| `agg()`       | Custom aggregation  | `df.agg({'A':'mean','B':'sum'})`      | Flexible summaries  | Great for multi-agg    |
| `transform()` | Transform per group | `df.groupby('col').transform('mean')` | Feature engineering | Keep same shape        |

---

## 🔹 13. **Apply & Map**

| Method       | Function                | Syntax                      | Usage          | Best Practice            |
| ------------ | ----------------------- | --------------------------- | -------------- | ------------------------ |
| `apply()`    | Apply function row/col  | `df.apply(np.sqrt)`         | Custom ops     | More general             |
| `applymap()` | Apply elementwise       | `df.applymap(lambda x:x*2)` | Element-level  | Use only on DataFrames   |
| `map()`      | Series-only elementwise | `df['col'].map(str.upper)`  | String cleanup | Use `map` for single col |

---

# ✅ Best Practices (Overall)

1. **Use `head()`, `info()`, `describe()` after loading any dataset.**
2. **Always handle missing data (`isna()`, `fillna()`) before analysis.**
3. **Use vectorized methods (`apply`, `map`) instead of Python loops** for speed.
4. **Prefer `merge` over manual joins**, and always specify `how=`.
5. **For big data:** check `memory_usage()`, convert text to `category`, and use chunked `read_csv()`.

---



## 📌 `isnull()` Recap

* `movies.isnull()` → returns a **DataFrame of booleans** (`True` if value is `NaN`, else `False`).

Example:

```python
import pandas as pd
import numpy as np

movies = pd.DataFrame({
    "title": ["A", "B", None, "C"],
    "year": [2000, None, 2002, None]
})
print(movies.isnull())
```

**Output**

```
   title   year
0  False  False
1  False   True
2   True  False
3  False   True
```

---

## 🔹 1. `movies[movies.isnull()==True].count()`

* Here you are **masking the DataFrame** with `movies.isnull()==True`.
* This replaces all non-NaN cells with `NaN`.
* Then `.count()` counts **non-null values per column** (not the `True`s!).

So this expression doesn’t really count nulls — it counts the surviving **non-null entries after masking**.

That’s why it gives weird results.

---

## 🔹 2. `movies.isnull().sum()`

* Here you directly sum the boolean DataFrame.
* In Pandas, `True = 1` and `False = 0`.
* So `.sum()` gives the **number of nulls per column** (the correct interpretation).

```python
print(movies.isnull().sum())
```

**Output**

```
title    1
year     2
dtype: int64
```

---

## ✅ Correct Way to Count Nulls

* Count per column:

```python
movies.isnull().sum()
```

* Count per row:

```python
movies.isnull().sum(axis=1)
```

* Count total missing values:

```python
movies.isnull().sum().sum()
```

---

## ⚠️ Best Practices

1. **Don’t use `movies[movies.isnull()==True]` for null counting** — it’s masking, not counting.
2. **Always use `.isnull().sum()`** → per column null counts.
3. For total null count, add another `.sum()`.

---

✅ So the difference is:

* `movies[movies.isnull()==True].count()` → counts non-null values after masking (misleading).
* `movies.isnull().sum()` → counts actual nulls (correct way).

---



# 📌 **Masking in Pandas**

## 🔹 1. Definition

👉 **Masking** means selecting or replacing values in a DataFrame/Series using a **boolean condition** (a mask).

* The **mask** is just a boolean array (True/False values) of the same shape as the data.
* Where the mask is `True`, the data is kept/used.
* Where the mask is `False`, the data is hidden/replaced (usually with `NaN`).

Think of it like **wearing a mask that only lets some values show through**.

---

## 🔹 2. Example of Masking in Pandas

```python
import pandas as pd
import numpy as np

df = pd.DataFrame({
    "name": ["A", "B", "C", "D"],
    "marks": [85, 40, 70, 90]
})

mask = df["marks"] > 60
print(mask)
```

**Output (the mask):**

```
0     True
1    False
2     True
3     True
Name: marks, dtype: bool
```

---

### ✅ Using the Mask to Filter Rows

```python
df[mask]
```

**Output:**

```
  name  marks
0    A     85
2    C     70
3    D     90
```

* Only rows where mask = `True` are kept.
* This is called **row masking** (boolean indexing).

---

### ✅ Masking with Replacement

```python
df.where(mask)
```

**Output:**

```
   name  marks
0     A   85.0
1   NaN    NaN
2     C   70.0
3     D   90.0
```

* Where mask = `True` → keep original values.
* Where mask = `False` → replace with `NaN`.

This is exactly what happened in your case with

```python
movies[movies.isnull()==True]
```

---

## 🔹 3. Key Methods Related to Masking

* `df[mask]` → keeps only `True` rows.
* `df.where(mask)` → keeps original where `True`, puts `NaN` where `False`.
* `df.mask(mask)` → the opposite → replaces `True` values with `NaN`.

---

## 🔹 4. Best Practices

* Always make sure your mask has the **same shape as the DataFrame/Series** you apply it to.
* Prefer `df.isnull()` or `df["col"] > x` for creating masks.
* Use `where`/`mask` when you want to **preserve DataFrame shape** (replace values with NaN instead of filtering rows out).

---

# ✅ In short

* **Masking = applying a boolean condition to data**.
* `True` → value is visible/kept,
* `False` → value is hidden/replaced (NaN).
* In Pandas:

  * `df[mask]` → filter rows.
  * `df.where(mask)` → mask values inside DataFrame.

---


