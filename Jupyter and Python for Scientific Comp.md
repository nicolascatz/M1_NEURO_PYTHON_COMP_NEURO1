# Jupyter and Python for Scientific Computing: A Practical Guide

---

## **Table of Contents**

1. [Why Use Jupyter Notebooks?](#why-jupyter)
2. [Python Basics for Scientific Computing](#python-basics)
3. [Data Structures: Lists, Tuples, Dictionaries](#data-structures)
4. [Control Flow: Loops and Conditionals](#control-flow)
5. [Functions and Scope](#functions)
6. [NumPy: The Swiss Army Knife for Scientific Computing](#numpy)
7. [Data Visualization with Matplotlib](#visualization)
8. [Error Handling and Debugging](#error-handling)
9. [Exercises and Solutions](#exercises)
10. [Best Practices and Tips](#best-practices)
11. [Further Resources](#resources)

---

&nbsp;

## **1. Why Use Jupyter Notebooks?**

Jupyter Notebooks are **interactive**, **reproducible**, and **collaborative** tools for:

- **Exploratory data analysis** (EDA).
- **Prototyping algorithms**.
- **Sharing code + explanations** in one document.

### **Key Features**


| Feature     | Description                                                          |
| ----------- | -------------------------------------------------------------------- |
| **Cells**   | Mix code, text (Markdown), math (LaTeX), and visualizations.         |
| **Kernel**  | Execute code in real-time (Python, R, Julia, etc.).                  |
| **Outputs** | Display plots, tables, and media inline.                             |
| **Sharing** | Export to HTML, PDF, or share via [nbviewer](https://nbviewer.org/). |


### **Basic Commands**


| Shortcut      | Action                    |
| ------------- | ------------------------- |
| `Shift+Enter` | Run cell, move to next.   |
| `Ctrl+Enter`  | Run cell, stay.           |
| `Esc + M`     | Convert cell to Markdown. |
| `Esc + Y`     | Convert cell to Code.     |
| `Esc + D + D` | Delete cell.              |


---

**⚠️ Pro Tip:**  
Always **restart your kernel** (`Kernel > Restart`) if your notebook behaves strangely (e.g., variables not updating).

---

&nbsp;

## **2. Python Basics for Scientific Computing**

Python is **simple**, **readable**, and **powerful** for scientific tasks.

### **2.1. Variables and Types**

Every value in Python is an **object** with a **type**:

```python
a = 1          # int
b = 1.0        # float
c = 'hello'    # str
d = True       # bool

print(type(a)) # Output: <class 'int'>
```

#### **Type Conversion**

Python **implicitly converts** types in operations:

```python
print(a + b)  # 2.0 (int + float → float)
```

But **explicit conversion** is safer:

```python
print(float(a) + b)  # Explicitly convert `a` to float
```

#### **Floating-Point Precision**

⚠️ **Warning:** Floats have limited precision!

```python
print(0.1 + 0.1 + 0.1 == 0.3)  # False (0.30000000000000004 != 0.3)
```

**Solution:** Use `math.isclose()` for float comparisons:

```python
import math
print(math.isclose(0.1 + 0.1 + 0.1, 0.3))  # True
```

---

### **2.2. Basic Operations**


| Operation      | Example  | Output |
| -------------- | -------- | ------ |
| Addition       | `1 + 2`  | `3`    |
| Multiplication | `3 * 4`  | `12`   |
| Exponentiation | `2 ** 3` | `8`    |
| Floor Division | `7 // 2` | `3`    |
| Modulus        | `7 % 2`  | `1`    |


---

**⚠️ Common Pitfall:**  
`1 / 2` returns `0.5` (float), but `1 // 2` returns `0` (floor division).

---

&nbsp;

## **3. Data Structures: Lists, Tuples, Dictionaries**

### **3.1. Lists**

**Ordered**, **mutable** collections:

```python
my_list = [1, 2.0, 'hello', True]
print(my_list[0])  # Output: 1
my_list[0] = 100   # Modify allowed
print(my_list)     # Output: [100, 2.0, 'hello', True]
```

#### **List Methods**


| Method     | Example                  | Description                  |
| ---------- | ------------------------ | ---------------------------- |
| `append()` | `my_list.append(4)`      | Add item to end.             |
| `pop()`    | `my_list.pop()`          | Remove and return last item. |
| `sort()`   | `my_list.sort()`         | Sort in place.               |
| `index()`  | `my_list.index('hello')` | Find index of item.          |


---

### **3.2. Tuples**

**Ordered**, **immutable** collections:

```python
my_tuple = (1, 2.0, 'hello')
# my_tuple[0] = 100  # Error: tuples are immutable!
```

**Use case:** When you need a **fixed collection** (e.g., coordinates).

---

### **3.3. Dictionaries**

**Key-value pairs**, unordered:

```python
my_dict = {'name': 'Alice', 'age': 30, 'city': 'Paris'}
print(my_dict['name'])  # Output: 'Alice'
my_dict['age'] = 31     # Modify value
my_dict['country'] = 'France'  # Add new key-value
```

#### **Dictionary Methods**


| Method     | Example               | Description                                      |
| ---------- | --------------------- | ------------------------------------------------ |
| `keys()`   | `my_dict.keys()`      | Return all keys.                                 |
| `values()` | `my_dict.values()`    | Return all values.                               |
| `items()`  | `my_dict.items()`     | Return key-value pairs.                          |
| `get()`    | `my_dict.get('name')` | Safe key access (returns `None` if key missing). |


---

&nbsp;

## **4. Control Flow: Loops and Conditionals**

### **4.1. `for` Loops**

Iterate over sequences:

```python
for i in [1, 2, 3]:
    print(i * 2)  # Indentation matters!
```

**Output:**

```
2
4
6
```

#### `**range()` Function**

Generate sequences:

```python
for i in range(5):       # 0 to 4
    print(i)
for i in range(2, 5):   # 2 to 4
    print(i)
for i in range(0, 10, 2): # 0 to 8, step 2
    print(i)
```

---

### **4.2. `while` Loops**

Repeat while a condition is `True`:

```python
count = 0
while count < 3:
    print(count)
    count += 1
```

---

**⚠️ Warning:**  
Always ensure your `while` loop has an **exit condition**, or it will run forever!

---

### **4.3. Conditionals**

Use `if`, `elif`, `else`:

```python
age = 18
if age < 13:
    print("Child")
elif age < 20:
    print("Teenager")
else:
    print("Adult")
```

#### **Ternary Operator**

Shorten simple conditionals:

```python
message = "Adult" if age >= 18 else "Minor"
```

---

&nbsp;

## **5. Functions and Scope**

### **5.1. Defining Functions**

Use `def` to create reusable code blocks:

```python
def greet(name):
    return f"Hello, {name}!"

print(greet("Alice"))  # Output: "Hello, Alice!"
```

#### **Default Arguments**

```python
def greet(name, greeting="Hello"):
    return f"{greeting}, {name}!"

print(greet("Bob", "Hi"))  # Output: "Hi, Bob!"
print(greet("Bob"))        # Output: "Hello, Bob!"
```

---

### **5.2. Variable Scope**

- **Local**: Inside a function.
- **Global**: Outside all functions.

```python
x = 10  # Global

def my_func():
    x = 5  # Local
    print(x)

my_func()  # Output: 5
print(x)   # Output: 10
```

**⚠️ Pitfall:**  
Avoid using global variables inside functions unless necessary.

---

### **5.3. Lambda Functions**

Short anonymous functions:

```python
square = lambda x: x ** 2
print(square(3))  # Output: 9
```

---

&nbsp;

## **6. NumPy: The Swiss Army Knife for Scientific Computing**

NumPy provides **fast, efficient arrays** and **mathematical functions**.

### **6.1. Creating Arrays**

```python
import numpy as np

# From a list
arr = np.array([1, 2, 3])

# Special arrays
zeros = np.zeros((2, 3))  # 2x3 array of zeros
ones = np.ones((2, 2))    # 2x2 array of ones
rand = np.random.rand(3)  # 3 random floats in [0, 1)
```

---

### **6.2. Array Operations**

```python
a = np.array([1, 2, 3])
b = np.array([4, 5, 6])

print(a + b)  # [5, 7, 9] (element-wise)
print(a * b)  # [4, 10, 18] (element-wise)
print(np.dot(a, b))  # 32 (dot product)
```

#### **Broadcasting**

NumPy automatically **broadcasts** operations on arrays of different shapes:

```python
print(a + 5)  # [6, 7, 8] (5 is added to each element)
```

---

### **6.3. Indexing and Slicing**

```python
arr = np.arange(10)  # [0, 1, 2, ..., 9]

print(arr[0])     # 0
print(arr[2:5])   # [2, 3, 4]
print(arr[:5])    # [0, 1, 2, 3, 4]
print(arr[::2])   # [0, 2, 4, 6, 8] (step 2)
```

#### **Boolean Indexing**

```python
print(arr[arr > 5])  # [6, 7, 8, 9]
```

---

### **6.4. Reshaping Arrays**

```python
arr = np.arange(6)
reshaped = arr.reshape((2, 3))
print(reshaped)
# Output:
# [[0 1 2]
#  [3 4 5]]
```

---

**⚠️ Warning:**  
Reshaping requires the **total number of elements** to remain the same.

---

### **6.5. Saving and Loading Arrays**

```python
np.save('my_array.npy', arr)
loaded_arr = np.load('my_array.npy')
print(loaded_arr)
```

---

&nbsp;

## **7. Data Visualization with Matplotlib**

Visualize data with **plots**, **histograms**, and **scatter plots**.

### **7.1. Basic Plot**

```python
import matplotlib.pyplot as plt

x = np.linspace(0, 10, 100)
y = np.sin(x)

plt.plot(x, y)
plt.title("Sine Wave")
plt.xlabel("x")
plt.ylabel("sin(x)")
plt.show()
```

### **7.2. Scatter Plot**

```python
x = np.random.rand(50)
y = np.random.rand(50)

plt.scatter(x, y, color='red')
plt.title("Random Scatter Plot")
plt.show()
```

### **7.3. Histogram**

```python
data = np.random.randn(1000)

plt.hist(data, bins=30, edgecolor='black')
plt.title("Normal Distribution")
plt.show()
```

---

**⚠️ Pro Tip:**  
Always **label your axes** and add a **title** to make plots interpretable!

---

&nbsp;

## **8. Error Handling and Debugging**

### **8.1. `try`/`except` Blocks**

Handle errors gracefully:

```python
try:
    result = 10 / 0
except ZeroDivisionError:
    print("Cannot divide by zero!")
else:
    print("Result:", result)
finally:
    print("Execution complete.")
```

### **8.2. Raising Exceptions**

```python
def divide(a, b):
    if b == 0:
        raise ValueError("Cannot divide by zero!")
    return a / b

try:
    print(divide(10, 0))
except ValueError as e:
    print(e)
```

---

**⚠️ Best Practice:**  
Use **specific exception types** (e.g., `ValueError`, `TypeError`) instead of catching all exceptions.

---

&nbsp;

## **9. Exercises and Solutions**

### **Exercise 1: Print Characters in a String**

**Task:** Write a function to print each character of a string on a new line.  
**Solution:**

```python
def print_chars(s):
    for char in s:
        print(char)

print_chars("hello")
```

---

### **Exercise 2: Double Vowels**

**Task:** Write a function to double each vowel in a string.  
**Solution:**

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

**Task:** Write a function to calculate the sum of integers from 1 to n.  
**Solution:**

```python
def sum_up_to(n):
    return n * (n + 1) // 2  # Mathematical formula

print(sum_up_to(10))  # 55
```

---

### **Exercise 4: Random Access to a 3D Array**

**Task:** Load a 3D array and access random elements.  
**Solution:**

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

&nbsp;

## **10. Best Practices and Tips**

### **10.1. Writing Clean Code**

- Use **descriptive variable names** (e.g., `num_students` instead of `n`).
- **Comment your code** to explain "why," not "what."
- **Modularize** your code into functions for reusability.

### **10.2. Jupyter-Specific Tips**

- **Use `%debug**` to debug errors interactively.
- **Restart the kernel** if variables behave unexpectedly.
- **Save frequently** (`Ctrl+S`) to avoid losing work.

### **10.3. Performance Tips**

- Use **vectorized operations** in NumPy instead of loops.
- Preallocate arrays when possible (e.g., `np.zeros()`).
- Use `**@` operator** for matrix multiplication (faster than `np.dot()` for large arrays).

---

**⚠️ Common Mistake:**  
Avoid using `for` loops with NumPy arrays when vectorized operations are possible.

---

&nbsp;

## **11. Further Resources**


| Resource                      | Link                                                                        |
| ----------------------------- | --------------------------------------------------------------------------- |
| Python Official Documentation | [docs.python.org/3](https://docs.python.org/3/)                             |
| NumPy User Guide              | [numpy.org/doc/stable/user](https://numpy.org/doc/stable/user/)             |
| Matplotlib Tutorial           | [matplotlib.org/stable/tutorials](https://matplotlib.org/stable/tutorials/) |
| Jupyter Notebook Basics       | [jupyter.org/documentation](https://jupyter.org/documentation)              |
| Scientific Python Ecosystem   | [scipy.org](https://scipy.org/)                                             |


---

### **Final Thoughts**

This tutorial covers the **essentials** of Jupyter and Python for scientific computing. To master these tools:

1. **Practice** with real datasets.
2. **Experiment** with new libraries (e.g., Pandas, SciPy).
3. **Share** your notebooks for feedback.

**Happy coding!** 🚀

---

**Feedback:**  
If you found this tutorial helpful, consider sharing it with colleagues or students. For questions or suggestions, feel free to ask!