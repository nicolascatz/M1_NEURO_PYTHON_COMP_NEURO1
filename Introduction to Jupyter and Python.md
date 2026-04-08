# Introduction to Jupyter and Python for Scientific Computing

---

## **1. Introduction to Jupyter Notebooks**

A **Jupyter Notebook** is an interactive environment that combines **code**, **formatted text** (Markdown), **mathematical equations**, and **visualizations**.

### **Basic Usage**

- **Double-click** a cell to edit it.
- **Execute** a cell with `Shift+Enter` or `Ctrl+Enter`.
- **Change cell type** (Code/Markdown) via the dropdown menu.
- **Markdown Formatting**:
  - `#` for headings, `-` for lists, `$...$` for LaTeX equations.

---

## **2. Getting Started with Python**

### **2.1. Basic Types and Variables**

In Python, everything is an **object** with a **type**:

- **Integers** (`int`), **floats** (`float`), **strings** (`str`), **booleans** (`bool`).

```python
a = 1          # int
b = 1.0        # float
c = 'char'     # str
d = True       # bool

print(type(a)) # Output: <class 'int'>
```

- **Addition**: Python automatically converts types when possible.
  ```python
  print(a + b) # 2.0 (int + float = float)
  ```
- **Equality**: Be careful with floats (limited precision)!
  ```python
  print(0.1 + 0.1 + 0.1 == 0.3) # False (0.30000000000000004 != 0.3)
  ```

---

### **2.2. Lists, Tuples, and Dictionaries**

- **List**: Ordered and mutable collection.
  ```python
  l = [a, b, c, d]
  print(l[0]) # Output: 1 (index 0)
  l[0] = 0.0  # Modification allowed
  ```
- **Tuple**: Ordered and **immutable** collection.
  ```python
  t = (a, b, c, d)
  # t[0] = 0.0  # Error: tuples are immutable!
  ```
- **Dictionary**: Collection of `key:value` pairs.
  ```python
  dic = {'weight': 12.3, 'height': 50.9}
  print(dic['weight']) # Output: 12.3
  ```

---

### **2.3. Loops and Conditionals**

- `**for` Loop**:
  ```python
  for i in [a, b, c, d]:
      print(i)  # Indentation is mandatory!
  ```
- `**range**`: Generates a sequence of integers.
  ```python
  for i in range(4):  # 0, 1, 2, 3
      print(i)
  ```
- **Conditionals**:
  ```python
  for i in [a, b, c, d]:
      if type(i) == int:
          print(f"{i} is an integer")
      else:
          print(f"{i} is not an integer")
  ```

---

### **2.4. Functions**

- **Definition** with `def`:
  ```python
  def double(x):
      return x + x

  print(double(a))  # Output: 2
  ```
- **Variable Scope**:
  ```python
  def shift(x):
      return x + e  # Error if `e` is not defined!

  e = -3
  print(shift(a))  # Output: -2
  ```

---

## **3. NumPy Library**

NumPy allows you to manipulate **multidimensional arrays** and perform efficient scientific computations.

### **3.1. NumPy Arrays**

- **Creation**:
  ```python
  import numpy as np
  x = np.array([0, 2, 8, -3])
  print(x.dtype)  # Data type of elements (e.g., int64)
  ```
- **Operations**:
  ```python
  y = np.array([10, 4, 6, 3])
  print(x + y)  # Element-wise addition
  print(x * y)  # Element-wise multiplication
  ```

### **3.2. Indexing and Slicing**

- **Accessing Elements**:
  ```python
  v = np.arange(0.0, 2.0, 0.4)  # [0.0, 0.4, 0.8, 1.2, 1.6]
  print(v[1:3])  # [0.4, 0.8]
  ```
- **Reshaping**:
  ```python
  A = np.arange(6).reshape([2, 3])  # [[0, 1, 2], [3, 4, 5]]
  ```

### **3.3. Saving and Loading**

- **Save**:
  ```python
  np.save('A.npy', A)
  ```
- **Load**:
  ```python
  C = np.load('A.npy')
  print(A == C)  # Check if arrays are identical
  ```

---

### **3.4. 2D and 3D Arrays**

- **Transpose**:
  ```python
  D = np.array([[0, 1, 2], [3, 4, 5]])
  print(D.T)  # [[0, 3], [1, 4], [2, 5]]
  ```
- **Boolean Indexing**:
  ```python
  sel_j = np.arange(74) < 10  # Boolean array
  M[:, sel_j, :].shape  # Select columns where sel_j is True
  ```

---

## **4. Exercises with Solutions**

### **Exercise 1: Print Characters in a String**

```python
def print_chars(s):
    for char in s:
        print(char)

print_chars("hello")
```

**Expected Output**:

```
h
e
l
l
o
```

---

### **Exercise 2: Double Vowels**

```python
def double_vowels(s):
    vowels = "aeiouAEIOU"
    result = []
    for char in s:
        if char in vowels:
            result.append(char * 2)
        else:
            result.append(char)
    return ''.join(result)

print(double_vowels("hello"))  # "heelloo"
```

---

### **Exercise 3: Sum of Integers from 1 to n**

```python
def sum_up_to(n):
    return n * (n + 1) // 2  # Mathematical formula

print(sum_up_to(10))  # 55
```

---

### **Exercise 4: Random Access to an Array**

```python
import numpy as np

M = np.load('BOLD_image.npy')

# 1. Random element
random_element = M[np.random.randint(0, M.shape[0]),
                   np.random.randint(0, M.shape[1]),
                   np.random.randint(0, M.shape[2])]
print(random_element)

# 2. Random subject (1st index)
random_subject = M[np.random.randint(0, M.shape[0]), :, :]
print(random_subject.shape)
```

---

## **5. Useful Resources**

- [Python Documentation](https://docs.python.org/3/)
- [NumPy Quickstart](https://numpy.org/doc/stable/user/quickstart.html)
- [Online Help](https://docs.python.org/3/reference/index.html) (`help(range)` in the interpreter)