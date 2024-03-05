> I won't add an index of heading at the top any longer.

> Recommend to check out the markdown version, which in GitHub can be viewed with a table of content.

# learning resources

## Python Offical "HowTo" Series

A few examples:
- [Logging HOWTO](https://docs.python.org/3.9/howto/logging.html)
- [Regular Expression HOWTO](https://docs.python.org/3.9/howto/regex.html#regular-expression-howto)
- [Sorting How to](https://docs.python.org/3.9/howto/sorting.html)                           

# Fundamentals
## [Null in Python: None](https://realpython.com/null-in-python/)

Python uses the keyword **None** to define *null* objects and variables.
As the *null* in Python, **None** is not defined to be 0 or any other value. 
In Python, **None** is an *object* and a first-class citizen

None is the value a function returns when there is no return statement in the function:

```Python
>>> def has_no_return():
...     pass
>>> has_no_return()
>>> print(has_no_return())
None
```

An important rule to keep in mind when you’re checking for None:

- Do use the identity operators is and is not.
- Do not use the equality operators == and !=.

The following objects are all falsy as well:

- None
- Empty lists
- Empty dictionaries
- Empty sets
- Empty strings
- 0
- False

Q: Does 'None' bind to a specific memory location? 

Q: `m=None` `n=None`, does `m=n`?

Q: 
```python
dummy.next = m = None
...
m = ListNode(4)
```
So does `dummy.next = ListNode(4)`?


```python
m = None
print(id(m))
n = None
print(id(n))

"""
None is a singleton. That is, the NoneType class only ever gives you the same single instance of None. 
There’s only one None in your Python program
"""
```

    4390759864
    4390759864





    '\nNone is a singleton. That is, the NoneType class only ever gives you the same single instance of None. \nThere’s only one None in your Python program\n'



In many other languages, null is just a synonym for 0, but null in Python is a full-blown object:
```Python
>>> type(None)
<class 'NoneType'>
```

In some languages, variables come to life from a **declaration**. They don’t have to have an initial value assigned to them. In those languages, the initial default value for some types of variables might be null. In Python, however, variables come to life from **assignment statements**.

```Python
>>> print(bar)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'bar' is not defined
>>> bar = None
>>> print(bar)
None
```

## [Assignment, Object and References in Python](https://realpython.com/python-variables/)


```python
"""
The built-in Python function id() returns an object’s integer identifier. 
Using the id() function, you can verify that two variables indeed point to the same object
"""

m = 300
n = 300
print(id(m))
print(id(n))
```

    4430456048
    4430455984



```python
"""
With the statement m = 300, Python creates an integer object with the value 300 and sets m as a reference to it. 
n is then similarly assigned to an integer object with value 300—but not the same object. 
"""

>>> m = 300
>>> n = 300
>>> id(m)
60062304
>>> id(n)
60062896
```




    60062896




```python
# But

>>> m = 30
>>> n = 30
>>> id(m)
1405569120
>>> id(n)
1405569120

"""
For purposes of optimization, the interpreter creates objects for the integers in the range [-5, 256] 
at startup, and then reuses them during program execution. Thus, when you assign separate variables to an 
integer value in this range, they will actually reference the same object.
"""
```

### id() return the "identity" of an object

Return the “identity” of an object. This is an integer which is **guaranteed to be unique** and constant for this object during its lifetime. Two objects with non-overlapping lifetimes may have the same id() value.

*CPython implementation detail*: **This is the address of the object in memory**.

# Number Basics

## What is the maximum possible value of an integer in Python ?

In Python, value of an integer is not restricted by the number of bits and can expand to the limit of the available memory (Sources : this and this). Thus we never need any special arrangement for storing large numbers (Imagine doing above arithmetic in C/C++).

As a side note, in Python 3, there is only one type “int” for all type of integers. In Python 2.7. there are two separate types “int” (which is 32 bit) and “long int” that is same as “int” of Python 3.x, i.e., can store arbitrarily large numbers.

```Python
# A Python program to show that there are two types in 
# Python 2.7 : int and long int 
# And in Python 3 there is only one type : int 
  
x = 10
print(type(x)) 
  
x = 10000000000000000000000000000000000000000000
print(type(x)) 

# Python 2
<type 'int'>
<type 'long'>

# Python 3
<type 'int'>
<type 'int'>
```


```python
x = 10
print(type(x)) 
  
x = 10000000000000000000000000000000000000000000
print(type(x)) 
```

    <class 'int'>
    <class 'int'>



```python
import sys
print(sys.maxsize)
```

    9223372036854775807



```python
help(divmod)
```

    Help on built-in function divmod in module builtins:
    
    divmod(x, y, /)
        Return the tuple (x//y, x%y).  Invariant: div*y + mod == x.
    


## [Round int](https://stackoverflow.com/a/19501343/1911726)

- general round()
- always round down
- round up

```Python
>>> import math
>>> math.floor(12.6)  # returns 12.0 in Python 2
12   
>>> int(12.6)
12
>>> math.trunc(12.6)
12
```

However, note that they behave differently with negative numbers: int and math.trunc will go to 0, whereas math.floor always floors downwards

```Python
>>> import math
>>> math.floor(-12.6)  # returns -13.0 in Python 2
-13
>>> int(-12.6)
-12
>>> math.trunc(-12.6)
-12
```

### [Tricky points about round()](https://realpython.com/python-rounding/)

```Python
>>> round(2.5)
2

>>> round(1.5)
2
```

[Another example](https://www.programiz.com/python-programming/methods/built-in/round)
```Python
print(round(2.665, 2))
print(round(2.675, 2))
>>>2.67
>>>2.67
```


## Check if a number is integer or decimal in Python

```Python
print(isinstance(i, int))
# True

print(isinstance(i, float))
# False

print(isinstance(f, int))
# False

print(isinstance(f, float))
# True
```

Check if *float* is integer

```Python
f = 1.23

print(f.is_integer())
# False

f_i = 100.0

print(f_i.is_integer())
# True
```

Check if string is integer

```Python
def is_integer(n):
    try:
        float(n)
    except ValueError:
        return False
    else:
        return float(n).is_integer()

print(is_integer(100))
# True

print(is_integer(100.0))
# True

print(is_integer(1.23))
# False

print(is_integer('100'))
# True

print(is_integer('100.0'))
# True

print(is_integer('1.23'))
# False

print(is_integer('string'))
# False
```

## Float and scientic notation



```python
ff = float(0.0519**-4)
print(ff)
g = 0.00001357
print(g)
print('using format str g:{:f}'.format(g))
```

    137825.81479394066
    1.357e-05
    using format str g:0.000014


## Ascii in Python

Unicode is a superset of ASCII, and the numbers 0–128 have the same meaning in ASCII as they have in Unicode.

### ord(c)

Given a string representing one Unicode character, return an integer representing the Unicode code point of that character. For example, ord(‘a’) returns the integer 97 and ord(‘€’) (Euro sign) returns 8364. This is the inverse of chr().

```Python
ord('A')  #--> 65
ord('B')  #--> 66
ord('C')  #--> 67
ord('a')  #--> 97
```

Reverse of ord() is chr()
```Python
chr(65)  #--> 'A'
chr(127) #--> '\x7f' memory address of [DEL] in hex
```

# Control Flow and Operator

### If...Else...

Simplier way to write:
```Python
if flag > 0:
    num = ...
else:
    num = ...

    
num = ... if flag>0 else ...
```

## For loop and break


```python
input = [1,2,3,4,7,6]

res = ''

for num in input:
    if num == 5:
        res = 'found'
        break
else:
    res = 'no found'
    
print(res)
```

    no fond



```python
input = [[1,2,3,4,7,6],[4,7],[5,8]]

res = []

for group in input:
    for num in group:
        if num == 5:
            res.append('found')
            break
    else:
        res.append('no found')
    
print(res)
```

    ['no found', 'no found', 'found']


### := walrus operator (since 3.8)


```python
a = list(range(12))
if (n := len(a)) > 10:
    print(f"List is too long ({n} elements, expected <= 10)")
```

    List is too long (12 elements, expected <= 10)


Some motivating use cases:

```Python
discount = 0.0
if (mo := re.search(r'(\d+)% discount', advertisement)):
    discount = float(mo.group(1)) / 100.0

# tmp variable for loop
while (block := f.read(256)) != '':
    process(block)

# in list comprehension
[clean_name.title() for name in names
 if (clean_name := normalize('NFC', name)) in allowed_names]
```

# Function Basics

## Positional-only parameters (since 3.8)

There is a new function parameter syntax / to indicate that some function parameters must be specified positionally and cannot be used as keyword arguments. This is the same notation shown by help() for C functions annotated with Larry Hastings’ Argument Clinic tool.

In the following example, parameters a and b are positional-only, while c or d can be positional or keyword, and e or f are required to be keywords:

```Python
def f(a, b, /, c, d, *, e, f):
    print(a, b, c, d, e, f)
```
The following is a valid call:

```Python
f(10, 20, 30, d=40, e=50, f=60)

# However, these are invalid calls:

f(10, b=20, c=30, d=40, e=50, f=60)   # b cannot be a keyword argument
f(10, 20, 30, 40, 50, f=60)           # e must be a keyword argument
```


```python
def outter():
    a = 12
    # count() # used after define count()
    def count():
        for i in range(a):
            print(i)
    count()
outter()
```

    0
    1
    2
    3
    4
    5
    6
    7
    8
    9
    10
    11



```python

def outter():
    b = 12

    def count():
        global b  # b should be declared outside of outter()
        for i in range(b):
            print(i)
    count()
outter()
```


    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    <ipython-input-19-c7140fc7a9e5> in <module>
          9             print(i)
         10     count()
    ---> 11 outter()
    

    <ipython-input-19-c7140fc7a9e5> in outter()
          8         for i in range(b):
          9             print(i)
    ---> 10     count()
         11 outter()


    <ipython-input-19-c7140fc7a9e5> in count()
          6     def count():
          7         global b
    ----> 8         for i in range(b):
          9             print(i)
         10     count()


    NameError: name 'b' is not defined



```python
b=12
def outter():
#     b = 12

    def count():
        global b  # b should be declared outside of outter()
        for i in range(b):
            print(i)
    count()
outter()
```

    0
    1
    2
    3
    4
    5
    6
    7
    8
    9
    10
    11



```python
def outter():
    c=12

    def count():
        # global c  
        
        for i in range(c):  # actually you don't need to declare global c
            print(i)
    count()
outter()
```

    0
    1
    2
    3
    4
    5
    6
    7
    8
    9
    10
    11



```python
def outter():
    d=5

    def count():
        nonlocal d  
        d=8
        for i in range(d):  # actually you don't need to declare global c
            print(i)
    count()
    print("d:", d) # nonlocal makes d come up from inner scope, covering d=5
outter()
```

    0
    1
    2
    3
    4
    5
    6
    7
    d: 8


## Lambda

[ref](https://realpython.com/python-testing/)
Definition

```Python
>>> lambda x: x
```

- The keyword: lambda
- A bound variable: x
- A body: x
    
Use `lambda` like an expression
```Python
>>> (lambda x: x + 1)(2)
3

>>> (lambda x, y: x + y)(2, 3)
5

>>> add_one = lambda x: x + 1
>>> add_one(2)
3
```

Check the inside of `lambda` and regular function
```Python
>>> import dis
>>> add = lambda x, y: x + y
>>> type(add)
<class 'function'>
>>> dis.dis(add)
  1           0 LOAD_FAST                0 (x)
              2 LOAD_FAST                1 (y)
              4 BINARY_ADD
              6 RETURN_VALUE
>>> add
<function <lambda> at 0x7f30c6ce9ea0>
```

Traceback

Arguments

```Python
>>> (lambda x, y, z: x + y + z)(1, 2, 3)
6
>>> (lambda x, y, z=3: x + y + z)(1, 2)
6
>>> (lambda x, y, z=3: x + y + z)(1, y=2)
6
>>> (lambda *args: sum(args))(1,2,3)
6
>>> (lambda **kwargs: sum(kwargs.values()))(one=1, two=2, three=3)
6
>>> (lambda x, *, y=0, z=0: x + y + z)(1, y=2, z=3)
6
```


Closure
```Python
def outer_func(x):
    y = 4
    return lambda z: x + y + z

for i in range(3):
    closure = outer_func(i)
    print(f"closure({i+5}) = {closure(i+5)}")
```


### Appropriate Uses of Lambda Expressions
- combined with `map()`, `filter()`, `reduce`
```Python
>>> list(map(lambda x: x.upper(), ['cat', 'dog', 'cow']))
['CAT', 'DOG', 'COW']
>>> list(filter(lambda x: 'o' in x, ['cat', 'dog', 'cow']))
['dog', 'cow']
>>> from functools import reduce
>>> reduce(lambda acc, x: f'{acc} | {x}', ['cat', 'dog', 'cow'])
'cat | dog | cow'
```
- key function in `.sort()` and `sorted()`
```Python
>>> ids = ['id1', 'id2', 'id30', 'id3', 'id22', 'id100']
>>> print(sorted(ids)) # Lexicographic sort
['id1', 'id100', 'id2', 'id22', 'id3', 'id30']
>>> sorted_ids = sorted(ids, key=lambda x: int(x[2:])) # Integer sort
>>> print(sorted_ids)
['id1', 'id2', 'id3', 'id22', 'id30', 'id100']
```
- UI framework
- Strongly suggest not to write lambda function with > 1 line
https://stackoverflow.com/questions/1233448/no-multiline-lambda-in-python-why-not

# Exception Handling

[Tutorial 1](https://www.programiz.com/python-programming/exception-handling)


```python
# import module sys to get the type of exception
import sys

randomList = ['a', 0, 2]

for entry in randomList:
    try:
        print("The entry is", entry)
        r = 1/int(entry)
        break
    except:
        print("Oops!", sys.exc_info()[0], "occured.")
        print("Next entry.")
        print()
print("The reciprocal of", entry, "is", r)
```

    The entry is a
    Oops! <class 'ValueError'> occured.
    Next entry.
    
    The entry is 0
    Oops! <class 'ZeroDivisionError'> occured.
    Next entry.
    
    The entry is 2
    The reciprocal of 2 is 0.5



```python
# Using raise

class Solution:
    def isCousins(self, root: TreeNode, x: int, y: int) -> bool:
        xh = yh = -10

        def getHeight(node):
            nonlocal xh, yh
            if not node:
                return 0

            lh = getHeight(node.left)
            rh = getHeight(node.right)
            height = 0

            if lh > rh:
                height = lh+1
            else:
                height = rh+1

            if xh > 0 and yh > 0:
                if node.left and node.right and \
                    ((node.left.val == x and node.right.val == y) or \
                    (node.right.val == y and node.right.val == x)):
                    # not cousin
                    raise Exception("No")
                if xh == yh:
                    # is cousin
                    raise Exception("Yes")
                else:
                    # not counsin
                    raise Exception("No")
            
            if node.val == x:
                xh = height
            if node.val == y:
                yh = height
            
            return height
        
        try:
            ret = getHeight(root)
        except Exception as exc:
            if str(exc) == 'Yes':
                return True
            else:
                return False

        return False
        
```

# Object Oriented Design (OOD)

### isinstance(object, classinfo)
Return True if the object argument is an instance of the classinfo argument, or of a (direct, indirect, or virtual) subclass thereof.

If classinfo is a tuple of type objects (or recursively, other such tuples) or a Union Type of multiple types, return True if object is an instance of any of the types.

### issubclass(class, classinfo)
Return True if class is a subclass (direct, indirect, or virtual) of classinfo. A class is considered a subclass of itself. 

### vars(object)
Return the __dict__ attribute for a module, class, instance, or any other object with a **__dict__** attribute.

Without an argument, vars() acts like locals().

A TypeError exception is raised if an object is specified but it doesn’t have a __dict__ attribute (for example, if its class defines the __slots__ attribute).

# I/O related

## interact with prompt

### input()
If the prompt argument is present, it is written to standard output without a trailing newline. The function then reads a line from input, converts it to a string (stripping a trailing newline), and returns that. When EOF is read, EOFError is raised.
```Python
>>> s = input("$$ ")
$$ What are you doing
>>> s
'What are you doing'
```
