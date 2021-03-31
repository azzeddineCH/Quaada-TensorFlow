# Introdcution to Numpy

Created: Feb 18, 2021 10:11 PM
Last Edited Time: Mar 20, 2021 10:51 PM
Status: done
Week: Week 1
presented: Yes

![https://upload.wikimedia.org/wikipedia/commons/thumb/3/31/NumPy_logo_2020.svg/1280px-NumPy_logo_2020.svg.png](https://upload.wikimedia.org/wikipedia/commons/thumb/3/31/NumPy_logo_2020.svg/1280px-NumPy_logo_2020.svg.png)

# What is Numpy ?

Numpy is one of the fundamental packages for scientific computing in Python by providing a solid and performente API for multi-dimentaional array operations including mathematical, logical, shape manipulation, sorting, selecting, I/O, discrete Fourier transforms, basic linear algebra, basic statistical operations, random simulation and much more.

```
import numpy as np

```

```
a = [ i for i in range(9)]
np_a = np.array(a)
np_a

```

a = [0, 1, 2, 3, 4, 5, 6, 7, 8]

# Numpy basics

## 1. Important Notes

- NumPy arrays have a fixed size at creation, unlike Python lists (which can grow dynamically).
- The elements in a NumPy array are all required to be of the same data type.

## 2. Numpy ndarray objects

the main object in Numpy id "ndarray" which is a multidimensional homogeneous array of ellements of the same type. indexed by a tuple of non-negative integeres that specify the position of the element among the diffrent axes (dimensions)

### 2.1 Object creation

```
a = [ 
      [1,2,3],
      [4,5,6]
    ]
a = np.array(a)# create a 2d matric array startin from a 2d python list
a 

```

```
a = [ 
      (1,2,3),
      (4,5,6)
    ]
a = np.array(a) # create a 2d matric array startin from a 2d python tuple
a 

```

```
a = np.arange(1,7).reshape(2,3) # create a 2d matric array startin from a range
a

```

### 2.2 Object attributes

the most important attribute of the ndarray object are the following:

```
# the number of axes (dimensions) of the array.
print(f"dim = {a.ndim}")

# the dimensions of the array.
print(f"shape = {a.shape}")

# the total number of elements of the array.
print(f"size = {a.size}")

# an object describing the type of the elements in the array.
print(f"type = {a.dtype}")

# the size in bytes of each element of the array. For example, an array of elements of type float64 has itemsize 8 (=64/8)
print(f"itemsize= {a.itemsize}")

```

### 3. Basic operations

```
# rehaping
a = np.arange(6) # array([0, 1, 2, 3, 4, 5]) with shape (,) and size 5
a = a.reshape((2,3)) # reshape a to (2,3) matric

```

```
# indexing
item_1 = a[1,2]
item_2 = a[-1,-1]
item_3 = a[1,-1]

```

```
# slicing
column_0 = a[:,0] # get the firt column
row_1 = a[1,:] # get the first row
column_0_1 = a[:,:2] # get the the first and second column

```

```
# iterating
for row in a: 
    elem = row[0] # select the first item of the row

```

```
# addition  

a = np.ones(6)
b = np.ones(6)

a  +  a # addition between two matrices
a  +  10 # addition between a matric and a scalar

```

```
# mutliplication  

a = np.ones(4) + 1 
b = np.ones(4) + 2

a  * b   # addition between two matrices element wise
a  * 10  # addition between a matric and a scalar

a = a.reshape((2,2))
b = b.reshape((2,2))
a.dot(b) # matric multiplication

```

```
# masking

a = np.arange(6)
a > 3
a[a > 3]

```

```
# reduction
a = np.arange(6).reshape((2,3))
a.reduce_max

```

# Why numpy is so valiable?...it is fast!

- Numpy prefroms operation in nearly C language time speed since np operation are mapped into a C interface
- Python is slower than C because it is an interpreted language.

```
def py_mul(s):
    a = [ i for i in range(s)]
    b = [2 for i in range(s)]
    c = []
    for elem_a, elem_b in zip(a,b):
        c.append(elem_a* elem_b)
  
    return c

```

```
def np_mul(s):
    a = np.arange(s)
    b = np.ones(s)*2
    c = a * b
    return c

```

```
sizes = [ 10**i for i in range(8)] # sampling matrices size
```

```
py_times = []
np_times = []

# calculate the required time for 1-d element wise multiplication using native py and numpy
for s in sizes: 
    start_time = time.time()
    np_mul(s)
    np_time = (time.time() - start_time)
    np_times.append(np_time)
  
    start_time = time.time()
    py_mul(s)
    py_time = (time.time() - start_time)
    py_times.append(py_time)

```

```
# plotting the results
import matplotlib.pyplot as plt 

plt.plot(sizes,py_times)
plt.plot(sizes,np_times)

plt.legend(["Python time in second", "Numpy time in second"])

```