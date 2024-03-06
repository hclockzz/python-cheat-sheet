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

### Underscore _ in Python
https://hackernoon.com/understanding-the-underscore-of-python-309d1a029edc

There are 5 cases for using the underscore in Python.
- For storing the value of last expression in interpreter.
- For ignoring the specific values. (so-called “I don’t care”)
- To give special meanings and functions to name of vartiables or functions.
- To use as ‘Internationalization(i18n)’ or ‘Localization(l10n)’ functions.
- To separate the digits of number literal value.


```python
# 1. When used in interpreter
>>> 10 
10 
>>> _ 
10 
>>> _ * 3 
30 
>>> _ * 20 
600
```




    600




```python
# 2. For Ignoring the values

# Ignore a value when unpacking
x, _, y = (1, 2, 3) # x = 1, y = 3 
x,y
```




    (1, 3)




```python
# Ignore the index
for _ in range(5):     
    print("Hi")
```

    Hi
    Hi
    Hi
    Hi
    Hi



```python
# 3. Give special meanings to name of variables and functions

# _single_leading_underscore

# This convention is used for declaring private variables, functions, methods and classes in a module. 
# Anything with this convention are ignored in from module import *. 

# However, of course, Python does not supports truly private, so we can not force somethings private ones 
# and also can call it directly from other modules. 

class _Base: # private class
    _hidden_factor = 2 # private variable
```


```python
# single_trailing_underscore_

# This convention could be used for avoiding conflict with Python keywords or built-ins. 
# You might not use it often.

list_ = List.objects.get(1) # Avoid conflict with 'list' built-in type

```


```python
# __double_leading_and_trailing_underscore__

# This convention is used for special variables or methods (so-called “magic method”) such as__init__, __len__. 
# These methods provides special syntactic features or does special things. 
# For example, __file__ indicates the location of Python file, __eq__ is executed when a == b expression is excuted. 

class A:
    def __init__(self, a): # use special method '__init__' for initializing
        self.a = a
```


```python
# 4. To separate the digits of number literal value

# This feature was added in Python 3.6. 
# It is used for separating digits of numbers using underscore for readability.

dec_base = 1_000_000
bin_base = 0b_1111_0000
hex_base = 0x_1234_abcd

print(dec_base) # 1000000
print(bin_base) # 240
print(hex_base) # 305441741
```

    1000000
    240
    305441741


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

### use `?` to get pydoc for a method


```python
chr?
```


    [0;31mSignature:[0m [0mchr[0m[0;34m([0m[0mi[0m[0;34m,[0m [0;34m/[0m[0;34m)[0m[0;34m[0m[0;34m[0m[0m
    [0;31mDocstring:[0m Return a Unicode string of one character with ordinal i; 0 <= i <= 0x10ffff.
    [0;31mType:[0m      builtin_function_or_method



```python
input?
```


    [0;31mSignature:[0m [0minput[0m[0;34m([0m[0mprompt[0m[0;34m=[0m[0;34m''[0m[0;34m)[0m[0;34m[0m[0;34m[0m[0m
    [0;31mDocstring:[0m
    Forward raw_input to frontends
    
    Raises
    ------
    StdinNotImplementedError if active frontend doesn't support stdin.
    [0;31mFile:[0m      ~/.pyenv/versions/3.10.13/lib/python3.10/site-packages/ipykernel/kernelbase.py
    [0;31mType:[0m      method


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

## Map, Filter and Reduce

### partial func

```Python
def rep(x, n):
    return [x for i in range(n)]
def repit(xs):
    rep3 = lambda x: rep(x, 3)
    return map(rep3, xs)

list(repit(['a',4,'J']))
>>> [['a', 'a', 'a'], [4, 4, 4], ['J', 'J', 'J']]
```

### map
Map applies a function to all the items in an input_list. Here is the blueprint:
`map(function_to_apply, list_of_inputs)`

```Python
items = [1, 2, 3, 4, 5]
squared = []
for i in items:
    squared.append(i**2)

# use map
squared = map(lambda x: x*2, items)
>>> squared
<map object at 0x102e54100>
>>> list(squared)
[2, 4, 6, 8, 10]
```

### filter
filter creates a list of elements for which a function returns true.

```Python
number_list = range(-5, 5)
less_than_zero = list(filter(lambda x: x < 0, number_list))
print(less_than_zero)

# Output: [-5, -4, -3, -2, -1]
```

### reduce
Reduce is a really useful function for performing some computation on a list and returning the result. It applies a rolling computation to sequential pairs of values in a list. For example, if you wanted to compute the product of a list of integers.
    
```Python
product = 1
list = [1, 2, 3, 4]
for num in list:
    product = product * num

# product = 24

# if use reduce
from functools import reduce
product = reduce(lambda a,b: a*b, list)
>>> product

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

## built-in methods for OO

### isinstance(object, classinfo)
Return True if the object argument is an instance of the classinfo argument, or of a (direct, indirect, or virtual) subclass thereof.

If classinfo is a tuple of type objects (or recursively, other such tuples) or a Union Type of multiple types, return True if object is an instance of any of the types.

### issubclass(class, classinfo)
Return True if class is a subclass (direct, indirect, or virtual) of classinfo. A class is considered a subclass of itself. 

### vars(object)
Return the __dict__ attribute for a module, class, instance, or any other object with a **__dict__** attribute.

Without an argument, vars() acts like locals().

A TypeError exception is raised if an object is specified but it doesn’t have a __dict__ attribute (for example, if its class defines the __slots__ attribute).

## Generators

### iterable, iterator, iteration

**iterable**
An iterable is any object in Python which has an __iter__ or a __getitem__ method defined which returns an iterator or can take indexes (You can read more about them here). In short an iterable is any object which can provide us with an iterator. 

**iterator**
An iterator is any object in Python which has a next (Python2) or __next__ method defined. That’s it. 


**iteration**
In simple words it is the process of taking an item from something e.g a list. When we use a loop to loop over something it is called iteration. It is the name given to the process itself. 



### generators

Generators are iterators, but you can only iterate over them once. It’s because they do not store all the values in memory, they generate the values on the fly. 

Why use generators:
- Generators are best for calculating large sets of results (particularly calculations involving loops themselves) where you don’t want to allocate the memory for all results at the same time.


```Python
def generator_function():
    for i in range(10):
        yield i

for item in generator_function():
    print(item)

# Output: 0
# 1
# 2
# 3
# 4
# 5
# 6
# 7
# 8
# 9
```


```python

```

# I/O related

## read from stdin

### input()
If the prompt argument is present, it is written to standard output without a trailing newline. The function then reads a line from input, converts it to a string (stripping a trailing newline), and returns that. When EOF is read, EOFError is raised.
```Python
>>> s = input("$$ ")
$$ What are you doing
>>> s
'What are you doing'
```

### `sys.stdin` 

Python sys module stdin is used by the interpreter for standard input. Internally, it calls the input() function. The input string is appended with a newline character (\n) in the end. So, you can use the rstrip() function to remove it.

```Python
import sys

for line in sys.stdin:
    if 'Exit' == line.rstrip():
        break
    print(f'Processing Message from sys.stdin *****{line}*****')
print("Done")
```


```python

```
