![NumPy Screenshot](https://github.com/Mostafa-Shariare/Python-Ml/blob/main/NumPy-Basics/Screenshot%20from%202025-08-31%2007-59-45.png?raw=true)


# NumPy Basics – A Beginner-Friendly Tutorial

NumPy (short for **Numerical Python**) is a core library for scientific and numerical computing in Python. It provides:

* High-performance **multi-dimensional arrays (ndarray)**
* Efficient **mathematical and logical operations**
* Support for **linear algebra, Fourier transforms, random numbers, and more**

Compared to Python lists, NumPy arrays are **faster, more memory-efficient, and optimized for numerical tasks**.

---

## Why NumPy?

NumPy arrays are preferable over Python lists for the following reasons:

1. **Speed** – NumPy operations are implemented in optimized C, making them much faster.
2. **Memory Efficiency** – Arrays use less memory compared to lists.
3. **Vectorization** – Operations can be applied directly to arrays without explicit loops.
4. **Multi-Dimensional Support** – Easy handling of matrices, tensors, and higher-dimensional data.
5. **Extensive Functionality** – Built-in functions for statistics, algebra, random numbers, etc.

---

## Python List vs NumPy Array Performance

The following example compares adding `5` to each element of a Python list vs a NumPy array:

```python
import numpy as np
from time import process_time

# Python list
python_list = [i for i in range(1000)]
start_time = process_time()
python_list = [i + 5 for i in python_list]
end_time = process_time()
print("Time with List:", end_time - start_time)

# NumPy array
np_array = np.array([i for i in range(1000)])
start_time = process_time()
np_array += 5
end_time = process_time()
print("Time with NumPy:", end_time - start_time)
```

**Demo Output (sample):**

```
Time with List: 0.001234
Time with NumPy: 3.7e-05
```

✅ NumPy is significantly faster due to **vectorized operations**.

---

## Creating NumPy Arrays

You can create NumPy arrays using the `np.array()` function.

```python
import numpy as np

# Python list
list1 = [1, 2, 3, 4]
print(list1, type(list1))

# NumPy array
np_array = np.array([1, 2, 3, 4, 5])
print(np_array, type(np_array))
```

**Demo Output:**

```
[1, 2, 3, 4] <class 'list'>
[1 2 3 4 5] <class 'numpy.ndarray'>
```

Notice that while lists and arrays look similar, NumPy arrays provide **enhanced capabilities**.

---

## Multi-Dimensional Arrays

NumPy can represent 2D arrays (matrices), 3D arrays, and beyond.

```python
b = np.array([(1, 2, 3, 4), (5, 6, 7, 8)])
print(b)
print("Shape:", b.shape)
```

**Demo Output:**

```
[[1 2 3 4]
 [5 6 7 8]]
Shape: (2, 4)
```

Here, `b` is a **2x4 matrix**.

* `.shape` returns the dimensions.

You can also specify the data type:

```python
c = np.array([(1, 2, 3, 4), (5, 6, 7, 8)], dtype=float)
print(c)
```

**Demo Output:**

```
[[1. 2. 3. 4.]
 [5. 6. 7. 8.]]
```

---

## Initial Placeholders in NumPy

NumPy provides convenient functions to create placeholder arrays:

```python
# Array of zeros
x = np.zeros((4, 5))
print(x)

# Array of ones
y = np.ones((3, 4))
print(y)

# Array filled with a specific value
z = np.full((4, 5), 5)
print(z)

# Identity matrix
a = np.eye(4)
print(a)
```

**Demo Output:**

```
[[0. 0. 0. 0. 0.]
 [0. 0. 0. 0. 0.]
 [0. 0. 0. 0. 0.]
 [0. 0. 0. 0. 0.]]

[[1. 1. 1. 1.]
 [1. 1. 1. 1.]
 [1. 1. 1. 1.]]

[[5 5 5 5 5]
 [5 5 5 5 5]
 [5 5 5 5 5]
 [5 5 5 5 5]]

[[1. 0. 0. 0.]
 [0. 1. 0. 0.]
 [0. 0. 1. 0.]
 [0. 0. 0. 1.]]
```

---

## Random Numbers in NumPy

NumPy’s random module is powerful for generating random data.

```python
# Random floats between 0 and 1
t = np.random.random((3, 4))
print(t)

# Random integers within a range
c = np.random.randint(10, 100, (3, 5))
print(c)
```

**Demo Output (sample):**

```
[[0.735 0.141 0.916 0.585]
 [0.876 0.457 0.352 0.221]
 [0.118 0.951 0.643 0.433]]

[[64 55 44 22 18]
 [99 72 61 11 35]
 [40 88 53 66 25]]
```

---

## Evenly Spaced Values

NumPy provides methods for generating evenly spaced ranges:

```python
# Using linspace (specify number of values)
d = np.linspace(10, 30, 5)
print(d)

# Using arange (specify step size)
e = np.arange(10, 30, 5)
print(e)
```

**Demo Output:**

```
[10. 15. 20. 25. 30.]
[10 15 20 25]
```

---

## Converting Lists to Arrays

You can easily convert Python lists into NumPy arrays:

```python
list2 = [10, 20, 20, 20, 50]
np_array = np.asarray(list2)
print(np_array, type(np_array))
```

**Demo Output:**

```
[10 20 20 20 50] <class 'numpy.ndarray'>
```

---

## Analyzing NumPy Arrays

```python
c = np.random.randint(10, 90, (5, 5))
print(c)

# Number of dimensions
print("Dimensions:", c.ndim)

# Number of elements
print("Size:", c.size)

# Data type
print("Data type:", c.dtype)
```

**Demo Output (sample):**

```
[[62 41 18 45 55]
 [73 38 20 64 14]
 [12 87 75 31 40]
 [48 56 23 77 52]
 [67 32 19 28 71]]
Dimensions: 2
Size: 25
Data type: int64
```

---

## Mathematical Operations

Python lists **concatenate** on addition:

```python
list1 = [1, 2, 3, 4, 5]
list2 = [6, 7, 8, 9, 10]
print(list1 + list2)
```

**Output:**

```
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
```

NumPy performs **element-wise operations** instead:

```python
a = np.random.randint(0, 10, (3, 3))
b = np.random.randint(10, 20, (3, 3))

print("a:\n", a)
print("b:\n", b)

print("Addition:\n", a + b)
print("Subtraction:\n", a - b)
print("Multiplication:\n", a * b)
print("Division:\n", a / b)
```

Or using NumPy functions:

```python
print(np.add(a, b))
print(np.subtract(a, b))
print(np.multiply(a, b))
print(np.divide(a, b))
```

**Demo Output (sample):**

```
a:
 [[3 7 2]
  [1 5 9]
  [4 6 0]]
b:
 [[17 15 14]
  [18 10 13]
  [12 19 16]]
Addition:
 [[20 22 16]
  [19 15 22]
  [16 25 16]]
Subtraction:
 [[-14  -8 -12]
  [-17  -5  -4]
  [ -8 -13 -16]]
Multiplication:
 [[51 105  28]
  [18  50 117]
  [48 114   0]]
Division:
 [[0.176 0.467 0.143]
  [0.056 0.5   0.692]
  [0.333 0.316 0.   ]]
```

---

## Array Transformations

### Transpose

```python
array = np.random.randint(0, 20, (2, 3))
print("Original:\n", array)
print("Transpose:\n", array.T)
```

**Demo Output:**

```
Original:
 [[ 2 14  7]
  [19  6 11]]
Transpose:
 [[ 2 19]
  [14  6]
  [ 7 11]]
```

---

### Reshaping Arrays

```python
a = np.random.randint(0, 10, (2, 3))
print("Original:\n", a, a.shape)

b = a.reshape(3, 2)
print("Reshaped:\n", b, b.shape)
```

**Demo Output:**

```
Original:
 [[5 8 3]
  [2 9 7]] (2, 3)
Reshaped:
 [[5 8]
  [3 2]
  [9 7]] (3, 2)
```

`.reshape()` changes the **shape** of the array without altering its data.

---

## 📚 Further Resources for Learning NumPy

* **Official NumPy Documentation**
  👉 [https://numpy.org/doc/](https://numpy.org/doc/)
  The best place to explore every function, example, and API reference.

* **NumPy User Guide**
  👉 [https://numpy.org/doc/stable/user/index.html](https://numpy.org/doc/stable/user/index.html)
  Beginner to advanced explanations, tutorials, and conceptual guides.

* **W3Schools NumPy Tutorial**
  👉 [https://www.w3schools.com/python/numpy\_intro.asp](https://www.w3schools.com/python/numpy_intro.asp)
  Easy-to-follow for beginners with lots of examples.

* **TutorialsPoint NumPy Tutorial**
  👉 [https://www.tutorialspoint.com/numpy/index.htm](https://www.tutorialspoint.com/numpy/index.htm)
  Step-by-step guide with simple explanations.

* **FreeCodeCamp NumPy Guide**
  👉 [https://www.freecodecamp.org/news/the-numpy-handbook/](https://www.freecodecamp.org/news/the-numpy-handbook/)
  A detailed blog-style handbook, perfect for learners.

* **Kaggle NumPy Micro-Course**
  👉 [https://www.kaggle.com/learn/numpy](https://www.kaggle.com/learn/numpy)
  Hands-on exercises and real-world examples.

* **GeeksforGeeks NumPy Tutorials**
  👉 [https://www.geeksforgeeks.org/python-numpy/](https://www.geeksforgeeks.org/python-numpy/)
  Beginner to intermediate level explanations with code snippets.

* **Book Recommendation**
  *Python for Data Analysis* by Wes McKinney (creator of Pandas) – has a strong introduction to NumPy.

---



