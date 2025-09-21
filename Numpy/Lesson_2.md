# <span style="color:darkcyan"> **Ways to Create NumPy Arrays**</span>

We’ll group them into categories:

1. **From existing data** (lists, tuples, other arrays)
2. **Based on shape (empty, zeros, ones, full, identity, etc.)**
3. **Based on sequences (arange, linspace, logspace, etc.)**
4. **Random values (uniform, normal, integers, etc.)**
5. **Copying & reshaping existing arrays**
6. **Specialized constructors (structured arrays, from buffer, etc.)**

---

## 1. From Existing Data

### 👉 `np.array()`

```python
import numpy as np

arr1 = np.array([1, 2, 3])              # 1D array
arr2 = np.array([[1, 2], [3, 4]])       # 2D array (matrix)
arr3 = np.array(((1,2,3),(4,5,6)))      # From tuple of tuples
```

### 👉 `np.asarray()`

(Similar to `array()`, but won’t copy if already an ndarray)

```python
arr = np.asarray([1, 2, 3])
```

---

## 2. Based on Shape

### 👉 Zeros

```python
np.zeros(5)                   # [0. 0. 0. 0. 0.]
np.zeros((2,3), dtype=int)    # 2x3 matrix of zeros
```

### 👉 Ones

```python
np.ones(4)                    # [1. 1. 1. 1.]
np.ones((3,3), dtype=float)   # 3x3 matrix of ones
```

### 👉 Full (custom fill)

```python
np.full((2,3), 7)             # 2x3 filled with 7
```

### 👉 Empty (uninitialized, fast but values are garbage)

```python
np.empty((2,2))               # Random uninitialized values
```

### 👉 Identity / Eye

```python
np.eye(3)                     # 3x3 identity matrix
np.identity(4, dtype=int)     # 4x4 identity
```

---

## 3. Based on Sequences

### 👉 `np.arange(start, stop, step)`

```python
np.arange(0, 10, 2)   # [0 2 4 6 8]
```

### 👉 `np.linspace(start, stop, num)`

```python
np.linspace(0, 1, 5)  # [0.   0.25 0.5  0.75 1. ]
```

### 👉 `np.logspace(start, stop, num, base=10)`

```python
np.logspace(1, 3, 4)  # [10. 100. 1000. 10000.]
```

---

## 4. Random Values

(All from `numpy.random`)

### 👉 Uniform distribution

```python
np.random.rand(3,2)       # random floats in [0,1)
```

### 👉 Normal distribution

```python
np.random.randn(3)        # 3 values from standard normal (mean=0, std=1)
```

### 👉 Random integers

```python
np.random.randint(0, 10, (2,3))  # 2x3 random ints in [0,10)
```

### 👉 Random choice

```python
np.random.choice([1, 2, 3, 4], size=5)   # Random picks from list
```

### 👉 Random uniform/normal with parameters

```python
np.random.uniform(5, 10, size=(2,3))     # Between 5 and 10
np.random.normal(50, 10, size=5)         # Mean=50, std=10
```

---

## 5. Copying & Reshaping

### 👉 `np.copy()`

```python
arr = np.array([1,2,3])
arr_copy = np.copy(arr)
```

### 👉 `np.reshape()`

```python
np.arange(12).reshape(3,4)
```

### 👉 `np.tile()` (repeats an array)

```python
np.tile([1,2], (3,2))   # Repeat [1,2] → 3x2
```

### 👉 `np.repeat()`

```python
np.repeat([1,2,3], 2)   # [1 1 2 2 3 3]
```

---

## 6. Specialized Constructors

### 👉 `np.fromfunction()`

(Constructs array using a function over indices)

```python
np.fromfunction(lambda i, j: i+j, (3,3), dtype=int)
# [[0 1 2]
#  [1 2 3]
#  [2 3 4]]
```

### 👉 `np.fromiter()`

```python
np.fromiter(range(5), dtype=int)
```

### 👉 `np.frombuffer()`

(From raw bytes)

```python
b = b'hello'
np.frombuffer(b, dtype='S1')
# ['h' 'e' 'l' 'l' 'o']
```

### 👉 Structured arrays (different dtypes per column)

```python
dt = np.dtype([('name', 'S10'), ('age', int)])
arr = np.array([("Alice", 25), ("Bob", 30)], dtype=dt)
```

---

## Quick Cheatsheet

| Category       | Function                                                    |
| -------------- | ----------------------------------------------------------- |
| From data      | `np.array`, `np.asarray`                                    |
| Shape-based    | `zeros`, `ones`, `full`, `empty`, `eye`, `identity`         |
| Sequence-based | `arange`, `linspace`, `logspace`                            |
| Random         | `rand`, `randn`, `randint`, `choice`, `uniform`, `normal`   |
| Reshape/Repeat | `reshape`, `copy`, `tile`, `repeat`                         |
| Advanced       | `fromfunction`, `fromiter`, `frombuffer`, structured arrays |

---

# <span style="color:darkcyan">**np.linspace()**</span>

```python
numpy.linspace(start, stop, num=50, endpoint=True, retstep=False, dtype=None, axis=0)
```

---

## **Parameters Explained**

1. **`start` (required)**

   - First value of the sequence.
   - Example: `0`

2. **`stop` (required)**

   - Last value of the sequence (included by default if `endpoint=True`).
   - Example: `10`

3. **`num` (optional, default = 50)**

   - Number of equally spaced samples.
   - Example: `num=5` → generates 5 numbers.

4. **`endpoint` (optional, default = True)**

   - If `True`: includes `stop`.
   - If `False`: excludes `stop` (like `range()`).

5. **`retstep` (optional, default = False)**

   - If `True`: returns a tuple `(array, step)`
   - Useful to know spacing between numbers.

6. **`dtype` (optional)**

   - Data type of output array.
   - Example: `dtype=int`

7. **`axis` (optional, default = 0)**

   - Axis along which values are stored when generating multidimensional arrays.

---

## **Examples**

### 👉 Basic usage

```python
import numpy as np

arr = np.linspace(0, 10, num=5)
print(arr)
```

Output:

```
[ 0.   2.5  5.   7.5 10. ]
```

➡ 5 numbers between 0 and 10 (inclusive).

---

### 👉 Excluding endpoint

```python
arr = np.linspace(0, 10, num=5, endpoint=False)
print(arr)
```

Output:

```
[0. 2. 4. 6. 8.]
```

➡ 5 numbers, evenly spaced, but **10 is excluded**.

---

### 👉 With `retstep=True`

```python
arr, step = np.linspace(0, 1, num=5, retstep=True)
print("Array:", arr)
print("Step:", step)
```

Output:

```
Array: [0.   0.25 0.5  0.75 1.  ]
Step: 0.25
```

➡ Confirms step size between consecutive numbers.

---

### 👉 With custom dtype

```python
arr = np.linspace(0, 5, num=6, dtype=int)
print(arr)
```

Output:

```
[0 1 2 3 4 5]
```

➡ Converts floating values to integers.

---

### 👉 Generating 2D with axis

```python
arr = np.linspace(0, 5, num=6, axis=0)
print(arr)
```

Output:

```
[0. 1. 2. 3. 4. 5.]
```

➡ Along axis 0 (default).
(If used inside multi-dimensional contexts, axis defines direction of filling.)

---

### 👉 Plotting Example (common in ML/DL)

```python
import matplotlib.pyplot as plt

x = np.linspace(0, 2*np.pi, 100)  # 100 points between 0 and 2π
y = np.sin(x)

plt.plot(x, y)
plt.title("Sine Wave")
plt.show()
```

➡ Smooth curve since `linspace` creates evenly spaced points.

---

## **When to Use `linspace()`**

- When you want **fixed number of points** in a range (e.g., 100 points between 0 and 1).
- Ideal for:

  - **Graph plotting**
  - **Sampling functions**
  - **Numerical simulations**

- Use `np.arange()` when you care about **step size** instead of number of points.

---

✅ **Quick Cheats**

- `np.linspace(0, 1, 5)` → `[0. , 0.25, 0.5 , 0.75, 1. ]`
- `np.linspace(0, 1, 5, endpoint=False)` → `[0. , 0.2 , 0.4 , 0.6 , 0.8 ]`
- `np.linspace(0, 1, 5, retstep=True)` → returns both array and step size.

---

