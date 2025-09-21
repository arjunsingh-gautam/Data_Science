# <span style="color:rebeccapurple">**Series Methods**</span>


| Method        | Syntax                                    | Use Case                  | Example              | Precaution                      |
| ------------- | ----------------------------------------- | ------------------------- | -------------------- | ------------------------------- |
| `pd.Series()` | `pd.Series(data, index=None, dtype=None)` | Create Series             | `pd.Series([1,2,3])` | Provide `dtype` for consistency |
| `.to_list()`  | `s.to_list()`                             | Convert to Python list    | `s.to_list()`        | Data type may change            |
| `.to_dict()`  | `s.to_dict()`                             | Convert to dictionary     | `s.to_dict()`        | Keys = index                    |
| `.to_frame()` | `s.to_frame(name=None)`                   | Convert to DataFrame      | `s.to_frame("col1")` | Use `name` for clarity          |
| `.astype()`   | `s.astype(dtype)`                         | Change data type          | `s.astype(float)`    | Beware of type errors           |
| `.copy()`     | `s.copy()`                                | Create deep copy          | `s.copy()`           | Use to avoid modifying original |
| `.array`      | `s.array`                                 | Underlying ExtensionArray | For advanced dtypes  | Not always NumPy                |

---

## **2. Indexing & Selection**

| Method    | Syntax                     | Use Case                    | Example         |
| --------- | -------------------------- | --------------------------- | --------------- |
| `.loc[]`  | `s.loc[label]`             | Access by label             | `s.loc['a']`    |
| `.iloc[]` | `s.iloc[pos]`              | Access by position          | `s.iloc[0]`     |
| `.at[]`   | `s.at[label]`              | Fast scalar access by label | `s.at['a']`     |
| `.iat[]`  | `s.iat[pos]`               | Fast scalar access by pos   | `s.iat[0]`      |
| `.get()`  | `s.get(key, default=None)` | Safe retrieval              | `s.get('x', 0)` |

---

## **3. Information & Summary**

| Method            | Syntax                        | Use Case                    | Example            | Best Practice              |
| ----------------- | ----------------------------- | --------------------------- | ------------------ | -------------------------- |
| `.head()`         | `s.head(n)`                   | First n rows                | `s.head(3)`        | Use for preview            |
| `.tail()`         | `s.tail(n)`                   | Last n rows                 | `s.tail(2)`        | Useful in time series      |
| `.sample()`       | `s.sample(n=, frac=)`         | Random sample               | `s.sample(2)`      | Use with `random_state`    |
| `.describe()`     | `s.describe()`                | Summary stats               | `s.describe()`     | Quick EDA                  |
| `.value_counts()` | `s.value_counts(dropna=True)` | Frequency count             | `s.value_counts()` | Good for categorical       |
| `.unique()`       | `s.unique()`                  | Unique values (NumPy array) | `s.unique()`       |                            |
| `.nunique()`      | `s.nunique(dropna=True)`      | Count unique                | `s.nunique()`      |                            |
| `.idxmax()`       | `s.idxmax()`                  | Index of max value          | `s.idxmax()`       | Only works if non-empty    |
| `.idxmin()`       | `s.idxmin()`                  | Index of min value          | `s.idxmin()`       |                            |
| `.equals()`       | `s.equals(other)`             | Compare two Series          | `s1.equals(s2)`    | Checks both values + index |

---

## **4. Mathematical & Statistical**

| Method       | Syntax          | Use Case           | Example       |
| ------------ | --------------- | ------------------ | ------------- |
| `.sum()`     | `s.sum()`       | Sum values         | `s.sum()`     |
| `.mean()`    | `s.mean()`      | Average            | `s.mean()`    |
| `.median()`  | `s.median()`    | Median             | `s.median()`  |
| `.mode()`    | `s.mode()`      | Most frequent      | `s.mode()`    |
| `.std()`     | `s.std()`       | Standard deviation | `s.std()`     |
| `.var()`     | `s.var()`       | Variance           | `s.var()`     |
| `.min()`     | `s.min()`       | Minimum            | `s.min()`     |
| `.max()`     | `s.max()`       | Maximum            | `s.max()`     |
| `.cumsum()`  | `s.cumsum()`    | Cumulative sum     | `s.cumsum()`  |
| `.cumprod()` | `s.cumprod()`   | Cumulative product | `s.cumprod()` |
| `.corr()`    | `s.corr(other)` | Correlation        | `s1.corr(s2)` |
| `.cov()`     | `s.cov(other)`  | Covariance         | `s1.cov(s2)`  |

⚠️ **Precaution:** Works only for **numeric dtypes**.

---

## **5. Missing Data Handling**

| Method           | Syntax                | Use Case                       | Example            |
| ---------------- | --------------------- | ------------------------------ | ------------------ |
| `.isna()`        | `s.isna()`            | Detect NaN (True/False)        | `s.isna()`         |
| `.notna()`       | `s.notna()`           | Opposite of isna               | `s.notna()`        |
| `.dropna()`      | `s.dropna()`          | Remove NaNs                    | `s.dropna()`       |
| `.fillna()`      | `s.fillna(value)`     | Replace NaN                    | `s.fillna(0)`      |
| `.replace()`     | `s.replace(old, new)` | Replace values                 | `s.replace(-1, 0)` |
| `.interpolate()` | `s.interpolate()`     | Fill missing via interpolation | `s.interpolate()`  |

---

## **6. String Handling** (via `.str` accessor)

| Method            | Syntax                   | Use Case             | Example |
| ----------------- | ------------------------ | -------------------- | ------- |
| `.str.lower()`    | `s.str.lower()`          | Convert to lowercase |         |
| `.str.upper()`    | `s.str.upper()`          | Uppercase            |         |
| `.str.contains()` | `s.str.contains("abc")`  | Pattern match        |         |
| `.str.replace()`  | `s.str.replace("a","b")` | Replace substrings   |         |
| `.str.len()`      | `s.str.len()`            | String length        |         |
| `.str.split()`    | `s.str.split(",")`       | Split string         |         |

⚠️ **Precaution:** Works only on **string/object dtype**.

---

## **7. Time Series Handling** (if Series has datetime dtype)

| Method           | Syntax                 | Use Case |
| ---------------- | ---------------------- | -------- |
| `.dt.year`       | Extract year           |          |
| `.dt.month`      | Extract month          |          |
| `.dt.day`        | Extract day            |          |
| `.dt.weekday`    | Day of week            |          |
| `.dt.strftime()` | Custom date formatting |          |

---

## **8. Reshaping & Combining**

| Method           | Syntax                          | Use Case            | Example                      |
| ---------------- | ------------------------------- | ------------------- | ---------------------------- |
| `.sort_values()` | `s.sort_values(ascending=True)` | Sort by values      |                              |
| `.sort_index()`  | `s.sort_index()`                | Sort by index       |                              |
| `.append()`      | `s.append(other)`               | Append Series       | Deprecated → use `pd.concat` |
| `.combine()`     | `s.combine(other, func)`        | Combine elementwise |                              |
| `.map()`         | `s.map(func)`                   | Apply function      | `s.map(lambda x: x*2)`       |
| `.apply()`       | `s.apply(func)`                 | Apply function      | `s.apply(abs)`               |
| `.where()`       | `s.where(cond, other)`          | Conditional replace |                              |
| `.mask()`        | `s.mask(cond, other)`           | Opposite of where   |                              |
| `.clip()`        | `s.clip(lower, upper)`          | Limit values        |                              |

---

## **9. Other Useful Utilities**

| Method               | Use Case               | Example                            |
| -------------------- | ---------------------- | ---------------------------------- |
| `.duplicated()`      | Find duplicates        | `s.duplicated()`                   |
| `.drop_duplicates()` | Remove duplicates      | `s.drop_duplicates()`              |
| `.rename()`          | Rename Series          | `s.rename("NewName")`              |
| `.pipe()`            | Functional chaining    | `s.pipe(func)`                     |
| `.explode()`         | Expand lists into rows | `pd.Series([[1,2],[3]]) → [1,2,3]` |

---

## **Best Practices**

✅ Always check `.dtype` before applying math/string/time functions.
✅ Use **vectorized methods** (`.map()`, `.apply()`) instead of Python loops.
✅ For missing values, decide carefully: **drop vs fill**.
✅ Use `.value_counts()` for quick categorical insights.
✅ For large Series, use `.memory_usage()` to optimize.

---

# 🔹 **Precautions**

⚠️ Many methods return **new Series**, not modify in-place (unless `inplace=True`).
⚠️ `append()` is **deprecated** → prefer `pd.concat`.
⚠️ `.str` methods fail if dtype ≠ object/string.
⚠️ `.dt` accessor works only on datetime dtype.

---

✅ **In short:** Pandas Series has **\~100 methods**, but if you master **creation, selection, summary, math, missing data, string, time**, you’ll cover **95% of real-world use cases**.

---

