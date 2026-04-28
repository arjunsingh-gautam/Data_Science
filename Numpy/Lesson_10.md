# **<span style="color:#FF6B6B">NumPy Indexing — Complete Breakdown</span>**

In **NumPy**, indexing is how you **access, filter, and manipulate data efficiently**.

There are **four major types of indexing**:

```text
1. Basic Indexing (Integer / Slice)
2. Fancy Indexing (Integer Array Indexing)
3. Boolean Indexing (Masking)
4. Mixed / Advanced Indexing
```

We’ll go **deep step-by-step (dry run + syntax + use cases + pitfalls)**.

---

# **<span style="color:#FFD166">1. Basic Indexing (Integer + Slice)</span>**

## **<span style="color:#66C2FF">What It Is</span>**

Access elements using:

```python
arr[index]
arr[start:stop:step]
```

---

## **<span style="color:#66C2FF">How It Works (Dry Run)</span>**

```python
import numpy as np
arr = np.array([10, 20, 30, 40, 50])
```

### **Single Index**

```python
arr[2]
```

Dry run:

```text
Index:  0   1   2   3   4
Value: 10  20  30  40  50
             ↑
```

Output:

```text
30
```

---

### **Slicing**

```python
arr[1:4]
```

Dry run:

```text
Take from index 1 to 3 (4 excluded)

Index:  0   1   2   3   4
Value: 10  20  30  40  50
         ↑   ↑   ↑
```

Output:

```text
[20 30 40]
```

---

## **<span style="color:#66C2FF">Syntax Rules</span>**

```python
arr[start : stop : step]
```

* start → inclusive
* stop → exclusive
* step → skip interval

---

## **<span style="color:#66C2FF">Use Cases</span>**

```text
subarrays
window operations
time-series slicing
feature selection
```

Example:

```python
last_3 = arr[-3:]
```

---

## **<span style="color:#66C2FF">Important Property</span>**

**Returns a VIEW (not a copy)**

```python
sub = arr[1:4]
sub[0] = 999
```

Now:

```text
arr = [10, 999, 30, 40, 50]
```

---

## **<span style="color:#66C2FF">Precautions</span>**

```text
modifying slice changes original array
```

To avoid:

```python
sub = arr[1:4].copy()
```

---

# **<span style="color:#FFD166">2. Fancy Indexing (Integer Array Indexing)</span>**

## **<span style="color:#66C2FF">What It Is</span>**

Selecting elements using **index arrays**.

```python
arr[[i1, i2, i3]]
```

---

## **<span style="color:#66C2FF">Dry Run</span>**

```python
arr = np.array([10, 20, 30, 40, 50])

arr[[0, 2, 4]]
```

Dry run:

```text
Pick index 0 → 10
Pick index 2 → 30
Pick index 4 → 50
```

Output:

```text
[10 30 50]
```

---

## **<span style="color:#66C2FF">2D Example</span>**

```python
arr = np.array([[1,2],
                [3,4],
                [5,6]])

arr[[0,2]]
```

Output:

```text
[[1 2]
 [5 6]]
```

---

## **<span style="color:#66C2FF">Key Behavior</span>**

**Returns a COPY (not a view)**

---

## **<span style="color:#66C2FF">Use Cases</span>**

```text
select specific rows
random sampling
reordering data
```

Example:

```python
batch = arr[[3, 1, 4]]
```

---

## **<span style="color:#66C2FF">Precautions</span>**

```text
creates copy → memory overhead
slower than slicing
```

---

# **<span style="color:#FFD166">3. Boolean Indexing (Masking)</span>**

## **<span style="color:#66C2FF">What It Is</span>**

Select elements using **True/False conditions**.

```python
arr[condition]
```

---

## **<span style="color:#66C2FF">Dry Run</span>**

```python
arr = np.array([10, 20, 30, 40, 50])

mask = arr > 25
```

Mask:

```text
[False False True True True]
```

Now:

```python
arr[mask]
```

Dry run:

```text
Pick values where mask = True
→ 30, 40, 50
```

Output:

```text
[30 40 50]
```

---

## **<span style="color:#66C2FF">Shortcut</span>**

```python
arr[arr > 25]
```

---

## **<span style="color:#66C2FF">Use Cases</span>**

```text
filter data
remove outliers
conditional selection
data cleaning
```

Example:

```python
arr[arr < 0] = 0
```

---

## **<span style="color:#66C2FF">Precautions</span>**

```text
mask size must match array size
creates copy (not view)
```

---

# **<span style="color:#FFD166">4. Mixed / Advanced Indexing</span>**

Combines:

```text
slicing + fancy indexing + boolean indexing
```

---

## **<span style="color:#66C2FF">Example</span>**

```python
arr = np.array([[10,20,30],
                [40,50,60],
                [70,80,90]])

arr[:, [0,2]]
```

---

## **<span style="color:#66C2FF">Dry Run</span>**

```text
: → all rows
[0,2] → select columns 0 and 2

Result:
[[10 30]
 [40 60]
 [70 90]]
```

---

## **<span style="color:#66C2FF">Another Example</span>**

```python
arr[arr > 50]
```

Select values:

```text
[60 70 80 90]
```

---

## **<span style="color:#66C2FF">Use Cases</span>**

```text
feature selection
column filtering
matrix operations
ML preprocessing
```

---

## **<span style="color:#66C2FF">Precautions</span>**

```text
mixing fancy indexing changes output shape
can be confusing
```

---

# **<span style="color:#FF6B6B">Key Differences (Important)</span>**

| Type             | Returns   | Speed   | Use Case           |
| ---------------- | --------- | ------- | ------------------ |
| Basic slicing    | View      | Fast    | subarrays          |
| Fancy indexing   | Copy      | Slower  | custom selection   |
| Boolean indexing | Copy      | Medium  | filtering          |
| Mixed indexing   | Copy/View | Complex | advanced selection |

---

# **<span style="color:#7DFFB3">Important Concepts You Must Remember</span>**

## **<span style="color:#66C2FF">1. View vs Copy</span>**

```text
Slicing → View
Fancy/Boolean → Copy
```

This affects:

```text
memory
performance
side effects
```

---

## **<span style="color:#66C2FF">2. Broadcasting Interaction</span>**

Boolean masks follow **broadcasting rules**.

Example:

```python
arr[arr > 10]
```

Condition applies element-wise.

---

## **<span style="color:#66C2FF">3. Shape Changes</span>**

Fancy indexing can change shape:

```python
arr[[0,2]]
```

Returns:

```text
new array (not same shape)
```

---

# **<span style="color:#7DFFB3">Final Intuition</span>**

Think of indexing like:

| Type             | Analogy                            |
| ---------------- | ---------------------------------- |
| Basic slicing    | cutting a piece from a ribbon      |
| Fancy indexing   | picking specific items from a list |
| Boolean indexing | filtering items based on condition |
| Mixed indexing   | combining filters + selections     |

---

If you want, I can next explain **NumPy broadcasting + vectorization (very important for ML pipelines)** which directly connects to **feature engineering and model performance optimization**.

