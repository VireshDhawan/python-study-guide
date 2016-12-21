# Python Study Guide
Python Study Guide

## Python Memory Management:
Use of private heap containing all Python objects and data structures.  User has no control, done by interpreter.

Raw memory allocator: Ensure enough memory from OS

Most work done by object-specific allocators. Objects are all treated differently, due to each needing storage requirements and space/speed tradeoffs

Heap space is allocated by Python/C API

## Python Garbage Collection:
Python object have reference count, count of objects pointing to it. when reference count is zero object is freed. Make use of reference cycles to find all objects that are unreachable. Unreachable objects include container objects: lists, dicts, instances, classes, tuples. Ints / Strings are not containers. Knows about each of these and c

## Python Data Structures
### List
Used for pretty much everything, ordered, any type of object
```python
list = [1, 2, 3]
list.insert(x)

#CAN ONLY USE .sort() ON LISTS

list.sort()
```

### Array
In Python, is small wrapper for C array (typically not used)

Represent basic values, chars, ints, floats, unicode. Corresponding varients for signed / unsigned
```python
from array import array

x = array('l', [1,2,6,8])
x.append(4)
#array('l', [1, 2, 6, 8, 4])
```

### Tuple
Values separated by a comma, values inside are **immutable**
```python
tuple = ‘hello’, 123, ‘world’
```

### Set
Unordered with no duplicates

```python
set = {‘apple’, ‘orange’, ‘apple’, ‘pear’}
print(set)
#‘apple’, ‘orange’, ‘pear’}
```

Can do relational algebra set operations on
```python
a = set(‘abracadabra’) 
b = set(‘alacazm’)
a - b
#‘r’, ‘d’, ‘b’}   etc etc
```

### Dictionary 
Dictionaries in Python are key: value pairs, unordered, implemented by a hashtable but used like hashmap

```python
tel = {‘jack’: 4098, ‘sape’: 4139}
tel[‘guido’] = 4127
#{‘sape’: 4139, ‘guido’:4127, ‘jack’: 4098}

# or use constructor
dict( [  (’sape’, 4139), (‘guido’, 4127), (‘jack’, 4098) ] )
```

### Sorting Data Structures
List uses .sort() to sort data for that instance

All other iterable data structures use sorted(), which returns a new sorted instance

Sort and sorted call timsort at C level, average complexity of O(n log n)

## Usage of * and ** for Passing Arbitrary Number of Arguments
\*: pass arbitrary number of arguments

\**: pass arbitrary number of dict values 

```python
def func(*args)
    . . .

def func(*args, **kwargs)
    . . .

#— or --
def func(x, y, z)
    . . .

list = [1,2,3]
function(*list)
dict = [‘x’:1, ‘y’:2, ‘z’:3]
function(**dict)
```