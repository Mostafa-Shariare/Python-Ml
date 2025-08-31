## Basic Tutorial of Numpy

NumPy (Numerical Python) is one of the most powerful and widely used libraries in Python for numerical computing. It provides support for large, multi-dimensional arrays and matrices, along with a wide collection of mathematical functions to operate on them.

If you’re coming from a pure Python background, you might be used to working with lists. However, Python lists are slow and not optimized for heavy numerical operations. That’s where NumPy shines – it makes mathematical computations faster, efficient, and more convenient.

Why Use NumPy?
Here are some key advantages of NumPy arrays over Python lists:

Faster Computations – NumPy uses optimized C code under the hood.

Memory Efficiency – NumPy arrays use less memory compared to Python lists.

Vectorized Operations – No need for loops; operations are applied element-wise.

Multi-Dimensional Arrays – Easy creation and manipulation of matrices, tensors, etc.

Rich Functionality – Mathematical, statistical, linear algebra, random number generation, and more.

List vs NumPy – Performance Check
Let’s compare how long it takes to add 5 to every element of a list vs a NumPy array.

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

NumPy executes operations much faster compared to lists because it uses vectorized computation and optimized memory usage.

Creating NumPy Arrays
import numpy as np

# Python list
list1 = [1, 2, 3, 4]
print(list1, type(list1))

# NumPy array
np_array = np.array([1, 2, 3, 4, 5])
print(np_array, type(np_array))

Output:

[1, 2, 3, 4] <class 'list'>
[1 2 3 4 5] <class 'numpy.ndarray'>

Notice the difference: NumPy arrays look similar to lists but allow faster and more powerful operations.



Multi-Dimensional Arrays
NumPy supports 2D arrays (matrices), 3D arrays, and beyond.

b = np.array([(1, 2, 3, 4), (5, 6, 7, 8)])
print(b)
print("Shape:", b.shape)

Output:

[[1 2 3 4]
 [5 6 7 8]]
Shape: (2, 4)

Here, we created a 2x4 matrix (2 rows, 4 columns).

.shape gives the dimensions.

We can also specify the data type:

c = np.array([(1, 2, 3, 4), (5, 6, 7, 8)], dtype=float)
print(c)



Initial Placeholders in NumPy
Sometimes, we need to create an array with predefined values (zeros, ones, etc.):

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

These functions are useful for initializing arrays before applying algorithms.



Random Numbers in NumPy
NumPy has powerful tools for generating random numbers:

# Random floats between 0 and 1
t = np.random.random((3, 4))
print(t)

# Random integers within a range
c = np.random.randint(10, 100, (3, 5))
print(c)



Evenly Spaced Values
# Using linspace (specify number of values)
d = np.linspace(10, 30, 5)
print(d)  # 5 numbers evenly spaced between 10 and 30

# Using arange (specify step size)
e = np.arange(10, 30, 5)
print(e)  # values from 10 to 30 with step of 5


🔹 Converting Lists to Arrays
list2 = [10, 20, 20, 20, 50]
np_array = np.asarray(list2)
print(np_array, type(np_array))



Analyzing NumPy Arrays
Let’s generate a random matrix and analyze it.

c = np.random.randint(10, 90, (5, 5))
print(c)

# Number of dimensions
print("Dimensions:", c.ndim)

# Number of elements
print("Size:", c.size)

# Data type
print("Data type:", c.dtype)



Mathematical Operations
Python lists concatenate when added, but NumPy arrays perform element-wise operations:

list1 = [1, 2, 3, 4, 5]
list2 = [6, 7, 8, 9, 10]
print(list1 + list2)  # Concatenates lists

With NumPy:

a = np.random.randint(0, 10, (3, 3))
b = np.random.randint(10, 20, (3, 3))

print(a)
print(b)

print("Addition:\n", a + b)
print("Subtraction:\n", a - b)
print("Multiplication:\n", a * b)
print("Division:\n", a / b)

Or using NumPy functions:

print(np.add(a, b))
print(np.subtract(a, b))
print(np.multiply(a, b))
print(np.divide(a, b))



Array Transformations
Transpose of an Array
array = np.random.randint(0, 20, (2, 3))
print(array)
print("Transpose:\n", array.T)

Reshaping Arrays
a = np.random.randint(0, 10, (2, 3))
print("Original:\n", a, a.shape)

b = a.reshape(3, 2)
print("Reshaped:\n", b, b.shape)

.reshape() changes the dimensions of an array without changing its data.
