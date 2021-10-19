# Topics:
- List
    - Sorting
- Tuple
- String
    - Regular expression

# Init a list


```python
lis = [0]*8
lis
```




    [0, 0, 0, 0, 0, 0, 0, 0]




```python
lis = list(range(1))
lis
```




    [0]



# Equality


```python
s = 'abc'
t = 'abc'

if list(s) == list(t):
    print('yes')
```

    yes


# index()/get index of a specific item from list


```python
# list.index(element, start, end)

# vowels list
vowels = ['a', 'e', 'i', 'o', 'i', 'u']

# index of 'e' in vowels
index = vowels.index('e')
print('The index of e:', index)

# element 'i' is searched
# index of the first 'i' is returned
index = vowels.index('i')

print('The index of i:', index)
```

    The index of e: 1
    The index of i: 2



```python
# alphabets list
alphabets = ['a', 'e', 'i', 'i', 'i', 'l', 'i', 'u']

index = alphabets.index('a')   
print('The index of a:', index)

# index of 'i' in alphabets
index = alphabets.index('e')   # 2
print('The index of e:', index)

# 'i' after the 4th index is searched
index = alphabets.index('i', 4)   # 6
print('The index of i:', index)

```

    The index of a: 0
    The index of e: 1
    The index of i: 4


## Lists Can Contain Arbitrary Objects
`a = [21.42, 'foobar', 3, 4, 'bark', False, 3.14159]`

Lists can even contain complex objects, like functions, classes, and modules


```python
stack = [[]]
stack.append([2,4])
pin = stack.pop()
pin
```




    [2, 4]




```python
class Node:
    val = "A certain node"
stack = []
node = Node()
stack.append((node,5))
pin = stack.pop()
pin
```




    (<__main__.Node at 0x10d2a7d10>, 5)




```python
print(pin[0].val)
```

    A certain node



```python
class Node:
    val = "A certain node"
stack = []
node = Node()
stack.append((node,5,[3]))
pin = stack.pop()
pin
```




    (<__main__.Node at 0x10d33ce90>, 5, [3])



### List of dictionaries

https://stackoverflow.com/questions/44994028/create-a-list-of-dictionaries


```python
# List of dictionaries

stack = [[]]
stack.append({"x":2,"y":4})
pin = stack.pop()
print("{} {}".format(pin["x"], pin["y"]))
```

    2 4


# If an element in List


```python
target = [1,2]
nums = [3,4,5,1,2,6]
if target in nums:
    print('yes')
else:
    print('no')
    
nums = [[3,4],[5],[1,2],[6]]
if target in nums:
    print('yes')
else:
    print('no')
```

    no
    yes


### If given a list of strings A, check if string B is a sub-string for any elements in A


```python
"""
Given: 
my_list = ['abc-123', 'def-456', 'ghi-789', 'abc-456']
Check if 'abc' in my_list

From: https://stackoverflow.com/a/4843172
A few ways
"""

# any
some_list = ['abc-123', 'def-456', 'ghi-789', 'abc-456']
if any("abc" in s for s in some_list):
    # whatever

    
>>> from  __builtin__ import any as b_any
>>> lst = ['yellow', 'orange', 'red']
>>> word = "or"
>>> b_any(word in x for x in lst)
True


# join all strings
>>> wordlist = ['yellow','orange','red']
>>> combined = '\t'.join(wordlist)

>>> 'or' in combined
True
>>> 'der' in combined
False


# filter
>>> lst = ['abc-123', 'def-456', 'ghi-789', 'abc-456']
>>> print filter(lambda x: 'abc' in x, lst)
['abc-123', 'abc-456']
```

# Init 2d list

https://stackoverflow.com/questions/6667201/how-to-define-a-two-dimensional-array-in-python


```python
# Creates a list containing 5 lists, each of 8 items, all set to 0
w, h = 5, 4;
Matrix = [[0 for x in range(w)] for y in range(h)] 
Matrix
```




    [[0, 0, 0, 0, 0], [0, 0, 0, 0, 0], [0, 0, 0, 0, 0], [0, 0, 0, 0, 0]]




```python
len(Matrix)
```




    5




```python
len(Matrix[0])
```




    8




```python
matrix = [[None]*4]*3
matrix
```




    [[None, None, None, None], [None, None, None, None], [None, None, None, None]]




```python
matrix[1][1]=2
matrix
```




    [[None, 2, None, None], [None, 2, None, None], [None, 2, None, None]]




```python
import numpy as np
numpy.zeros((3, 5))
```




    array([[0., 0., 0., 0., 0.],
           [0., 0., 0., 0., 0.],
           [0., 0., 0., 0., 0.]])




```python
Matrix[0][1]
```




    0



Write a Python program which takes two digits m (row) and n (column) as input and generates a two-dimensional array. The element value in the i-th row and j-th column of the array should be i*j.

Note :  
i = 0,1.., m-1   
j = 0,1, n-1.


```python
def generate2D(m, n):
    matrix = [[0 for i in range(n)] for j in range(m)]
    
    for i in range(m):
        for j in range(n):
            matrix[i][j] = i*j
    
    for row in matrix:
        print(row)

generate2D(3,5)
```

    [0, 0, 0, 0, 0]
    [0, 1, 2, 3, 4]
    [0, 2, 4, 6, 8]


## Range()


```python
li1 = list(range(7,-1,-1))
print(li1)

li = list(range(6//2,-1,-1))
print(li)
```

    [7, 6, 5, 4, 3, 2, 1, 0]
    [3, 2, 1, 0]


# Enumerate ()


```python
nums = [11, 19, 21, 24, 25, 27]
for i,num in enumerate(nums,1):
    print(i,num)
```

    1 11
    2 19
    3 21
    4 24
    5 25
    6 27



```python
nums = [11, 19, 21, 24, 25, 27]
for i,num in enumerate(nums):
    print(i,num)
```

    0 11
    1 19
    2 21
    3 24
    4 25
    5 27


# iter()

A good example to use iter can be:

```
def func():
    element = next(arr) # so each time visit different element, useful when building binary tree
    visit element

arr = iter(a certain list)
```


```python
# list of vowels
vowels = ['a', 'e', 'i', 'o', 'u']
vowels_iter = iter(vowels)

print(next(vowels_iter))    # 'a'
print(next(vowels_iter))    # 'e'
print(next(vowels_iter))    # 'i'
print(next(vowels_iter))    # 'o'
print(next(vowels_iter))    # 'u'
```

    a
    e
    i
    o
    u



```python
# Check if iter() is empty, you can use for

vowels = ['a', 'e', 'i', 'o', 'u']
vowels_iter = iter(vowels)

for vowel in vowels_iter:
    print(vowel)
```

# Tild ~ operator in List


```python
for i in range(0, len(nums)):
    print(nums[~i])
```

    27
    25
    24
    21
    19
    11


# Generate random int list


```python
import numpy as np
```


```python
def list_sum(numbers)->int:
    sum = 0
    for item in numbers:
        sum+=item
    return sum

numbers = np.random.randint(0,20,5)
# print(numbers.array.split(numbers,','))
print(list(numbers))

# list_sum(numbers)
```

    [18, 15, 11, 7, 14]



```python
def list_production(numbers) -> int:
    product = 1
    for item in numbers:
        product *= item
    return product
    
numbers = np.random.randint(1,20,6)
print(numbers)
list_production(numbers)
```

    [ 2 17 16  4  1 15]





    32640




```python
def get_max_list(numbers) -> int:
    max = numbers[0]
    for item in numbers:
        if item > max:
            max = item
    return max
    
numbers = np.random.randint(1,20,6)
print(numbers)
get_max_list(numbers)
```

    [11 17 10  4  2 14]





    17




```python
# generate 6 numbers, ranging between 1-30

arr = np.random.randint(1,30,6)
np.sort(arr)
```




    array([11, 19, 21, 24, 25, 27])



## generate binary numbers

list only contain 0 or 1


```python
import numpy as np
np.random.randint(2, size=10)
```




    array([1, 1, 0, 0, 1, 0, 1, 1, 0, 0])




```python

np.random.randint(2, size=(8,8))
```




    array([[0, 1, 0, 1, 0, 1, 1, 1],
           [1, 0, 0, 0, 0, 1, 1, 1],
           [0, 0, 1, 0, 1, 0, 0, 1],
           [0, 1, 1, 1, 0, 0, 1, 1],
           [1, 1, 0, 1, 0, 1, 0, 1],
           [0, 1, 1, 0, 0, 1, 0, 0],
           [0, 1, 0, 0, 1, 1, 0, 1],
           [1, 1, 1, 1, 0, 1, 1, 0]])




```python
np.random.choice([0, 1], size=(8,8), p=[1./4, 3./4])
```




    array([[1, 1, 1, 1, 1, 0, 1, 1],
           [0, 1, 1, 1, 1, 1, 1, 1],
           [1, 1, 1, 1, 1, 1, 0, 1],
           [1, 1, 0, 1, 1, 1, 1, 0],
           [1, 0, 1, 1, 1, 1, 1, 0],
           [1, 1, 1, 1, 1, 1, 0, 1],
           [1, 1, 1, 1, 1, 1, 1, 1],
           [0, 0, 0, 1, 1, 1, 1, 1]])




```python
matrix = [[1, 0, 1, 0, 1, 1, 0, 0],
       [0, 1, 1, 1, 1, 0, 0, 1],
       [1, 0, 1, 1, 1, 0, 1, 0],
       [1, 1, 1, 1, 1, 0, 1, 1],
       [1, 0, 1, 1, 1, 0, 0, 0],
       [1, 1, 1, 1, 0, 1, 1, 1],
       [0, 0, 1, 1, 0, 0, 0, 0],
       [1, 1, 1, 0, 1, 0, 0, 0]]
matrix
```




    [[1, 0, 1, 0, 1, 1, 0, 0],
     [0, 1, 1, 1, 1, 0, 0, 1],
     [1, 0, 1, 1, 1, 0, 1, 0],
     [1, 1, 1, 1, 1, 0, 1, 1],
     [1, 0, 1, 1, 1, 0, 0, 0],
     [1, 1, 1, 1, 0, 1, 1, 1],
     [0, 0, 1, 1, 0, 0, 0, 0],
     [1, 1, 1, 0, 1, 0, 0, 0]]




```python
np.random.choice(["0", "1"], size=(2,2), p=[1./4, 3./4])
```




    array([['1', '1'],
           ['1', '1']], dtype='<U1')



# Adding items


```python
li = [11, 19, 21, 24, 25, 27]
print(li+[31])
```

    [11, 19, 21, 24, 25, 27, 31]



```python
li.insert(-1,28)
li
```




    [11, 19, 21, 24, 25, 28, 27]




```python
li.insert(0, 7)
print(li)

li.insert(0, 9)
print(li)
```

    [7, 11, 19, 21, 24, 25, 27]
    [9, 7, 11, 19, 21, 24, 25, 27]


# Remove item
- remove()
- pop()
- del


```python
# The remove() method removes the specified item:

thislist = ["apple", "banana", "cherry"]
# thislist.remove("banana")
print(thislist.remove("banana"))
print(thislist)
```

    None
    ['apple', 'cherry']



```python
# The pop() method removes the specified index, (or the last item if index is not specified):

thislist = ["apple", "banana", "cherry"]
thislist.pop()
print(thislist)
```

    ['apple', 'banana']



```python
# The del keyword removes the specified index:

thislist = ["apple", "banana", "cherry"]
del thislist[0]
print(thislist)
```

    ['banana', 'cherry']



```python
# The del keyword can also delete the list completely:

thislist = ["apple", "banana", "cherry"]
del thislist
thislist
```


    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    <ipython-input-18-8f550f36b72e> in <module>
          3 thislist = ["apple", "banana", "cherry"]
          4 del thislist
    ----> 5 thislist
    

    NameError: name 'thislist' is not defined



```python
# The clear() method empties the list:


thislist = ["apple", "banana", "cherry"]
thislist.clear()
print(thislist)
```

    []


## Add commas between list elements


```python
list(numbers) # add comma betweens nums in numbers
numbers
```




    array([11, 17, 10,  4,  2, 14])



# List slicing



```python
numbers = [11, 17, 10,  4,  2, 14]
nums = list(numbers)
print(nums[1:3])
print(nums[:1])
```

    [17, 10]
    [11]



```python
nums = [10, 12]
print(nums[:2])
```

    [10, 12]



```python
li = [8,7,2]
print(li[1:3])
print(li[2:])
```

    [7, 2]
    [2]



```python
[8,5,1,7,10,12]
```


```python
li = [11, 17, 10]
li[:5]
```




    [11, 17, 10]




```python
# slicing array with 2 elements

li = [11,4]
mid = int(len(li)/2)
print(li[0:mid])
print(li[mid:])
```

    [11]
    [4]



```python
# slicing array with only 1 element

li = [11]
mid = int(len(li)/2)
print(li[0:mid])
print(li[mid:])
```

    []
    [11]



```python
for i in range(2,3):
    print(i)
```

    2



```python
string = "Hello"
print(string[:-5])
print(string[-5:])
```

    
    Hello


## Reverse list order


```python
for i in range(2,n-1).reverse()
    print(i)
```


      File "<ipython-input-25-a3e92cfab943>", line 1
        for i in range(2,n-1).reverse()
                                       ^
    SyntaxError: invalid syntax




```python
lis = list(range(2,10))
lis
```




    [2, 3, 4, 5, 6, 7, 8, 9]




```python
list(range(-1,-1,-1))
```




    []




```python
list(range(1,0,-1))
```




    [1]




```python
for i in reversed(lis):
    print(i)
```

    9
    8
    7
    6
    5
    4
    3
    2



```python
def reverse(lis): 
    return stakc

reverse_lis = reverse(lis)
reverse_lis
```




    [9, 8, 7, 6, 5, 4, 3, 2]



### Slicing explanation

Here is a bit of an [explanation](https://stackoverflow.com/questions/48638951/list-in-reverse-order-python) of the [::-1] operation:

Slicing notation is of the format [start_point:end_point:step]

- The start_point is not specified, this becomes the length of the list so the operation starts at the end.
- The end_point is also not specified, this becomes -1 so the operation will end at the start.
- The step is -1, so it will iterate backwards in steps of 1 (i.e. every element of the list).

This will create a shallow copy of your original list. This means the list you pass into reverse(s) will remain the same.

```
>>> x = [1, 2, 3]
>>> y = x[::-1]
>>> x
[1, 2, 3]
>>> y
[3, 2, 1]
```

To be exercise:

[items()](https://www.geeksforgeeks.org/python-dictionary-items-method/)

[append and extend](https://www.geeksforgeeks.org/append-extend-python/)

[Python scope](https://www.w3schools.com/python/python_scope.asp)


# Minimum and Maximum


```python
import numpy as np

def get_max_list(numbers) -> int:
    max = numbers[0]
    for item in numbers:
        if item > max:
            max = item
    return max
    
numbers = np.random.randint(1,20,6)
print(numbers)
get_max_list(numbers)
```

    [ 3 14 15 15  1 11]





    15




```python
li =[2, 5, 1, 3, 4]
print(min(li))
print(max(li))
```

    1
    5


## List comprehension


```python
li = [2,5,1,3,4]

lk = [val for val in li]
lk
```




    [2, 5, 1, 3, 4]




```python
if 5 in lk:
    print("Yes")
else:
    print("No")
```

    Yes



```python
def rep(x,n):
    return [x for i in range(1, n+1)]

rep(3,5)
```




    [3, 3, 3, 3, 3]




```python
def odd(x):
    if x/2 == 0:
        return False
    else:
        return True
    
def substite(xs):
    return ["BOOM!" if x < 10 else "BANG!" for x in xs if odd(x)]

substite([1,3,4,1,2,35,1])
```




    ['BOOM!', 'BOOM!', 'BOOM!', 'BOOM!', 'BOOM!', 'BANG!', 'BOOM!']



*Question:* Does a formula exist for list comprehension?


```python
chr?
```


```python
# return a list upper case from A to Z
upperCase = [chr(i) for i in range(ord('A'),ord('Z')+1)]
def removeNonUpperCase(st):
    return [c for c in st if c in upperCase]

removeNonUpperCase('AFkajflASDFfla;K')
```




    ['A', 'F', 'A', 'S', 'D', 'F', 'K']



## Partial funtions


```python
def rep(x, n):
    return [x for i in range(n)]
def repit(xs):
    rep3 = lambda x: rep(x, 3)
    return map(rep3, xs)

list(repit(['a',4,'J']))
```




    [['a', 'a', 'a'], [4, 4, 4], ['J', 'J', 'J']]



## Filter


```python
filter(lambda x: x>3, [1,5,3,2,1,6,4,3,2])
```




    <filter at 0x106523910>




```python
xgreter3 = list(filter(lambda x: x>3, [1,5,3,2,1,6,4,3,2]))
xgreter3
```




    [5, 6, 4]



## Reduce


```python

from math import sqrt
from functools import reduce
def stdDev(A):
    add = lambda x, y: x+y
    N = float(len(A))
    mu = reduce(add, A, 0)/N
    tot = reduce(add, [(a - mu)**2 for a in A], 0) 
    return sqrt(tot/N)

print(stdDev([13, 23, 12, 44, 55]))
```


```python
def forall(A):
    return reduce(lambda x, y:  x and y, A, True)

print(forall([True, True, True, True]))
print(forall([True, True, False, True]))
```

    True
    False



```python
def sum2():
    return reduce(lambda x, y:  x+y, range(1, 6), 0)

sum2()
```




    15




```python
def countEver():
    return sum([1 for n in range(0,6) if n%2 == 0])

countEver()
```




    3




```python
def indexSet(x, B):
    for index, b in enumerate(B):
        if x == b:
            return index
    return -1

indexSet(3,[4,6,1,2,3,7,8])
```




    4




```python
# wrong
def indexSet(x, B):
    return sum([1 for b in B if b!=x])

indexSet(3,[4,6,1,2,3,7,8])
```




    6




```python
from functools import reduce

def indexSet(t, B):
    return reduce(lambda x, y: x+1 if (y!=t), B,0)

indexSet(3,[4,6,1,2,3,7,8])
```


      File "<ipython-input-6-a865aab46b80>", line 4
        return reduce(lambda x, y: x+1 if (y!=t), B,0)
                                                ^
    SyntaxError: invalid syntax




```python
def indexSet(x,B):
    return filter(lambda b: b == x, B)

list(indexSet(3,[4,6,1,2,3,7,8]))
```




    [3]



# Flatten list

reference:
[stack overflow](https://stackoverflow.com/questions/952914/how-to-make-a-flat-list-out-of-list-of-lists)


```python
from pandas.core.common import flatten

li = [1,[4,[6]]]
# li = []
iter_li = iter(li)

print(list(flatten(li)))
print(isinstance(li[1], list))    
```

    [1, 4, 6]
    True



```python
import itertools

li_1 = [1,[4,[6]]]
flatten = itertools.chain.from_iterable
list(flatten(li_1))
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-25-c6a0d972e2ee> in <module>
          3 li_1 = [1,[4,[6]]]
          4 flatten = itertools.chain.from_iterable
    ----> 5 list(flatten(li_1))
    

    TypeError: 'int' object is not iterable


## Sum a list


```python
li = [3,1,2,4,2,4,7]
sum(li)
```




    23




```python
# get the square sum

sum([int(i) ** 2 for i in li])
```




    99




```python
# Partial sum
li = [3,1,2,4,2,4,7]
sum(li[0:3])
```




    6




```python
matrix = [[1,3,1],[1,5,1],[4,2,1]]
sum([matrix[i][0] for i in range(1,3)])
```




    5




```python
sum(matrix[0][:0])
```




    0



# Yield generator


```python
def infinite_sequence():
    num = 0
    while True:
        yield num
        num += 1
```


```python
gen = infinite_sequence()
```


```python
next(gen)
```




    0




```python
next(gen)
```




    1




```python
next(gen)
```




    2




```python
for i in range(1,20):
    print(next(gen))
```

    22
    23
    24
    25
    26
    27
    28
    29
    30
    31
    32
    33
    34
    35
    36
    37
    38
    39
    40



```python
nums_squared_lc = [num**2 for num in range(5)]
nums_squared_lc
```




    [0, 1, 4, 9, 16]




```python
# use () instead of [], you get a generator

nums_squared_gc = (num**2 for num in range(5))
nums_squared_gc
```




    <generator object <genexpr> at 0x104f6a6d0>




```python
import sys
nums_squared_lc = [i * 2 for i in range(10000)]
sys.getsizeof(nums_squared_lc)
```




    87632




```python
nums_squared_gc = (i ** 2 for i in range(10000))
print(sys.getsizeof(nums_squared_gc))
```

    128


## Get the mean of a list


```python
li = [-2,1,-3,4,-1,2,1,-5,4]
sum(li)/(len(li))
```




    0.1111111111111111




```python
li[:-1]
```




    [-2, 1, -3, 4, -1, 2, 1, -5]



# String and list


```python
s = []
s.append(str(1))
s.append("()")
res = ''.join(s)
res
```




    '1()'




```python
t = ''

if not t:
    print("empty string")

if t == '':
    print("empty string too")

if t is None:
    print("empty string as well")
```

    empty string
    empty string too


# Split a list with strings using delimiter


```python
def Convert(string): 
    li = list(string.split(" ")) 
    return li 
  
# Driver code     
str1 = "Geeks for Geeks"
print(Convert(str1)) 
```

    ['Geeks', 'for', 'Geeks']



```python
# delimiter is hyphen 
def Convert(string): 
    li = list(string.split("-")) 
    return li 
  
# Driver code     
str1 = "Geeks-for---Geeks"
print(Convert(str1)) 
```

    ['Geeks', 'for', '', '', 'Geeks']



```python
words = ['Geeks', 'for', '', '', 'Geeks']
print(words)
print('|'.join(words))
```

    ['Geeks', 'for', '', '', 'Geeks']
    Geeks|for|||Geeks


# Split a word string into list of characters


```python
# method 1
def split(word): 
    return [char for char in word]  
      
# Driver code 
word = 'geeks'
print(split(word))
```

    ['g', 'e', 'e', 'k', 's']



```python
# method 2
def split(word): 
    return list(word) 
      
# Driver code 
word = 'geeks'
print(split(word)) 
```

    ['g', 'e', 'e', 'k', 's']



```python
sorted(list('eat'))
```




    ['a', 'e', 't']



# Convert a list of characters into a string word


```python
s = ['a', 'b', 'c', 'd']
str_s = ''.join(s)
str_s
```




    'abcd'




```python
# Python program to convert a list 
# of character 
  
def convert(s): 
  
    # initialization of string to "" 
    new = "" 
  
    # traverse in the string  
    for x in s: 
        new += x  
  
    # return string  
    return new 
      
      
# driver code    
s = ['g', 'e', 'e', 'k', 's', 'f', 'o', 'r', 'g', 'e', 'e', 'k', 's'] 
print(convert(s)) 
```

    geeksforgeeks



```python
b = "Hello, World!"
len(b)
```




    13




```python
b[:-1]
```




    'Hello, World'



# Intersection between two lists

https://stackoverflow.com/questions/3697432/how-to-find-list-intersection


```python
# Python program to illustrate the intersection 
# of two lists using set() and intersection() 
def Intersection(lst1, lst2): 
    return set(lst1).intersection(lst2) 
      
# Driver Code 
lst1 = [ 4, 11, 1, 17, 9, 26, 28, 28, 26, 66, 91] 
lst2 = [11, 4, 74, 21, 45, 1, 63] 
print(set(lst1))
print(Intersection(lst1, lst2)) 
```

    {1, 66, 4, 9, 11, 17, 26, 91, 28}
    {1, 11, 4}



```python
list1 = [1,7,3,4,5,6]

list2 = [7,4,6,9,10]

list(filter(lambda x:x in list1, list2))
```




    [7, 4, 6]



## Zip() method:
usage
- make two list behaves like a dict, [How do I convert two lists into a dictionary?](https://stackoverflow.com/a/209854/1911726)


```python
keys = ['a', 'b', 'c']
values = [1, 2, 3]
kv = zip(keys, values)
print(type(kv))

```

    <class 'zip'>



```python
dictionary = dict(zip(keys, values))
print(dictionary) # {'a': 1, 'b': 2, 'c': 3}
dictionary['a']
```

    {'a': 1, 'b': 2, 'c': 3}





    1




```python
# convert to a n*2 list of list
kv_list = list(zip(keys, values))
print(kv_list) 
kv_list[0][0]
```

    [('a', 1), ('b', 2), ('c', 3)]





    'a'



# Sort a list

https://www.geeksforgeeks.org/python-list-sort/


```python
# L.sort() works for list only, sorted works for iterable
# .sort() returns None and modifies the values in place
```


```python
numbers = [1, 3, 4, 2] 
  
# Sorting list of Integers in ascending 
numbers.sort() 
  
print(numbers) 
```

    [1, 2, 3, 4]



```python
numbers = [1, 3, 4, 2] 
  
# Sorting list of Integers in descending 
numbers.sort(reverse = True) 
  
print(numbers)
```

    [4, 3, 2, 1]



```python
# Sorting user using user defined order.

# Python program to demonstrate sorting by user's 
# choice 
  
# function to return the second element of the 
# two elements passed as the parameter 
def sortSecond(val): 
    return val[1]  
  
# list1 to demonstrate the use of sorting  
# using using second key  
list1 = [(1, 2), (3, 3), (1, 1)] 
  
# sorts the array in ascending according to  
# second element 
list1.sort(key = sortSecond)  
print(list1) 
  
# sorts the array in descending according to 
# second element 
list1.sort(key = sortSecond, reverse = True) 
print(list1) 
```

    [(1, 1), (1, 2), (3, 3)]
    [(3, 3), (1, 2), (1, 1)]



```python
li = [0, 1, -1]
li.sort()
print(li)
```

    [-1, 0, 1]


### sort a string


```python

s = 'abad'
print(s.sort())
```


    ---------------------------------------------------------------------------

    AttributeError                            Traceback (most recent call last)

    <ipython-input-1-40c59f5b5297> in <module>
          2 
          3 s = 'abad'
    ----> 4 print(s.sort())
    

    AttributeError: 'str' object has no attribute 'sort'



```python
s = 'abad'
print(sorted(s))
```

    ['a', 'a', 'b', 'd']


### sorted()
https://realpython.com/python-sort/
- The function sorted() did not have to be defined. It’s a built-in function that is available in a standard installation of Python.
- sorted(), with no additional arguments or parameters, is ordering the values in numbers in an ascending order, meaning smallest to largest.


```python
numbers = [6, 9, 3, 1]
print(sorted(numbers))

numbers

```

    [1, 3, 6, 9]





    [6, 9, 3, 1]




```python
numbers_tuple = (6, 9, 3, 1)
numbers_set = {5, 5, 10, 1, 0}
numbers_tuple_sorted = sorted(numbers_tuple)
numbers_set_sorted = sorted(numbers_set)
numbers_tuple_sorted

numbers_set_sorted
```




    [0, 1, 5, 10]




```python
>>> names = ['Harry', 'Suzy', 'Al', 'Mark']
>>> sorted(names)
['Al', 'Harry', 'Mark', 'Suzy']
>>> sorted(names, reverse=True)
['Suzy', 'Mark', 'Harry', 'Al']
```




    ['Suzy', 'Mark', 'Harry', 'Al']




```python
# key argument expects a function to be passed to it
```


```python
>>> word = 'paper'
>>> len(word)
5
>>> words = ['banana', 'pie', 'Washington', 'book']
>>> sorted(words, key=len)
['pie', 'book', 'banana', 'Washington']
```




    ['pie', 'book', 'banana', 'Washington']



## About cmp

If I have to think sorting in a way of comparator, I can use `functools.cmp_to_key`.

[functools.cmp_to_key(func)](https://docs.python.org/3/library/functools.html#functools.cmp_to_key):
- Transform an old-style comparison function to a key function. Used with tools that accept key functions (such as **sorted(), min(), max(), heapq.nlargest(), heapq.nsmallest(), itertools.groupby())**. This function is primarily used as a transition tool for programs being converted from Python 2 which supported the use of comparison functions.

- A comparison function is any callable that accept two arguments, compares them, and *returns a negative number for less-than, zero for equality, or a positive number for greater-than*. A key function is a callable that accepts one argument and returns another value to be used as the sort key.


```python
# An example from Medium
# https://medium.com/@peteryun/algo-sorting-python-compararor-c237ad9f76e2

from functools import cmp_to_key


class Player:
    def __init__(self, name, score):
        self.name = name
        self.score = score

    def comparator(a, b):
        if a.score == b.score:
            if a.name > b.name:
                return 1
            else:
                return -1
        else:
            return b.score - a.score


n = int(input())
data = []
for i in range(n):
    name, score = input().split()
    score = int(score)
    player = Player(name, score)
    data.append(player)

data = sorted(data, key=cmp_to_key(Player.comparator))
for i in data:
    print(i.name, i.score)
```

How I use `cmp_to_key` solve keetcode 937


```python
class Solution:
    def reorderLogFiles(self, logs: List[str]) -> List[str]:
        if not logs:
            return []
        
        keys = []
        for i, log in enumerate(logs):
            words = log.split(" ")
            key = ','.join(words[1:])
            # print(key)
            keys.append( (str(key), i) )
            
        def order(x,y):
            if x[0][0].isalpha():
                if y[0][0].isnumeric():
                    return -1
                elif y[0][0].isalpha():
                    if x[0] < y[0]:
                        return -1
                    elif x[0] > y[0]:
                        return 1
                    else:
                        log1, log2 = logs[x[1]], logs[y[1]]
                        id1, id2 = log1.split(" ")[0], log2.split(" ")[0]
                        if id1 < id2:
                            return -1
                        elif id1 > id2:
                            return 1
                        else:
                            return 0
            elif x[0][0].isnumeric():
                if y[0][0].isalpha():
                    return 1
                elif y[0][0].isnumeric():
                    # "The digit-logs should be put in their original order."
                    return -1 if x[1] < y[1] else 1
        
        # print(keys)
        keys.sort(key=functools.cmp_to_key(order))
        # print(keys)
        
        res = []
        for entry in keys:
            ind = entry[1]
            res.append(logs[ind])
        
        return res
```


```python

```

# Underscore _ in Python
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
for _ in range(10):     
    print("Hi")
```

    Hi
    Hi
    Hi
    Hi
    Hi
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


    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    <ipython-input-66-9aa075fcec2d> in <module>
          4 # You might not use it often.
          5 
    ----> 6 list_ = List.objects.get(1) # Avoid conflict with 'list' built-in type
    

    NameError: name 'List' is not defined



```python
# __double_leading_underscore

class A:
    def _single_method(self):
        pass
    
class B(A):
    def __double_method(self): # for mangling
        pass
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


# Tuple

**list** is unhashable, alternatively, we can use tuple.


```python
# Different types of tuples

# Empty tuple
my_tuple = ()
print(my_tuple)

# Tuple having integers
my_tuple = (1, 2, 3)
print(my_tuple)

# Tuple having integers
my_tuple = ([4,5])
print(my_tuple)

# tuple with mixed datatypes
my_tuple = (1, "Hello", 3.4)
print(my_tuple)

# nested tuple
my_tuple = ("mouse", [8, 4, 6], (1, 2, 3))
print(my_tuple)
```

    ()
    (1, 2, 3)
    [4, 5]
    (1, 'Hello', 3.4)
    ('mouse', [8, 4, 6], (1, 2, 3))



```python
"""
A tuple can also be created without using parentheses. This is known as tuple packing.
"""

my_tuple = 3, 4.6, "dog"
print(my_tuple)

# tuple unpacking is also possible
a, b, c = my_tuple

print(a)      # 3
print(b)      # 4.6
print(c)      # dog
```

    (3, 4.6, 'dog')
    3
    4.6
    dog



```python
"""
Creating a tuple with one element is a bit tricky.

Having one element within parentheses is not enough. 
We will need a trailing comma to indicate that it is, in fact, a tuple.
"""

my_tuple = ("hello")
print(type(my_tuple))  # <class 'str'>

# Creating a tuple having one element
my_tuple = ("hello",)
print(type(my_tuple))  # <class 'tuple'>

# Parentheses is optional
my_tuple = "hello",
print(type(my_tuple))  # <class 'tuple'>
```

    <class 'str'>
    <class 'tuple'>
    <class 'tuple'>


## Access Tuple Elements

1. Indexing
2. Negative Indexing
3. Slicing


```python
# Accessing tuple elements using indexing
my_tuple = ('p','e','r','m','i','t')

print(my_tuple[0])   # 'p' 
print(my_tuple[5])   # 't'

# IndexError: list index out of range
# print(my_tuple[6])

# Index must be an integer
# TypeError: list indices must be integers, not float
# my_tuple[2.0]

# nested tuple
n_tuple = ("mouse", [8, 4, 6], (1, 2, 3))

# nested index
print(n_tuple[0][3])       # 's'
print(n_tuple[1][1])       # 4
```

    p
    t
    s
    4



```python
# Accessing tuple elements using slicing
my_tuple = ('p','r','o','g','r','a','m','i','z')

# elements 2nd to 4th
# Output: ('r', 'o', 'g')
print(my_tuple[1:4])

# elements beginning to 2nd
# Output: ('p', 'r')
print(my_tuple[:-7])

# elements 8th to end
# Output: ('i', 'z')
print(my_tuple[7:])

# elements beginning to end
# Output: ('p', 'r', 'o', 'g', 'r', 'a', 'm', 'i', 'z')
print(my_tuple[:])
```

    ('r', 'o', 'g')
    ('p', 'r')
    ('i', 'z')
    ('p', 'r', 'o', 'g', 'r', 'a', 'm', 'i', 'z')


## Changing a Tuple

Unlike lists, tuples are immutable.


```python
# Changing tuple values
my_tuple = (4, 2, 3, [6, 5])


# TypeError: 'tuple' object does not support item assignment
# my_tuple[1] = 9

# However, item of mutable element can be changed
my_tuple[3][0] = 9    # Output: (4, 2, 3, [9, 5])
print(my_tuple)

# Tuples can be reassigned
my_tuple = ('p', 'r', 'o', 'g', 'r', 'a', 'm', 'i', 'z')

# Output: ('p', 'r', 'o', 'g', 'r', 'a', 'm', 'i', 'z')
print(my_tuple)
```

    (4, 2, 3, [9, 5])
    ('p', 'r', 'o', 'g', 'r', 'a', 'm', 'i', 'z')


We can use + operator to combine two tuples. This is called concatenation.

We can also repeat the elements in a tuple for a given number of times using the * operator.

Both + and * operations result in a new tuple.


```python
# Concatenation
# Output: (1, 2, 3, 4, 5, 6)
print((1, 2, 3) + (4, 5, 6))

# Repeat
# Output: ('Repeat', 'Repeat', 'Repeat')
print(("Repeat",) * 3)
```

    (1, 2, 3, 4, 5, 6)
    ('Repeat', 'Repeat', 'Repeat')


### Deleting a Tuple

```Python
# Deleting tuples
my_tuple = ('p', 'r', 'o', 'g', 'r', 'a', 'm', 'i', 'z')

# can't delete items
# TypeError: 'tuple' object doesn't support item deletion
# del my_tuple[3]

# Can delete an entire tuple
del my_tuple

# NameError: name 'my_tuple' is not defined
print(my_tuple)
```

### Tuple method

```Python
my_tuple = ('a', 'p', 'p', 'l', 'e',)

print(my_tuple.count('p'))  # Output: 2
print(my_tuple.index('l'))  # Output: 3


# Membership test in tuple
my_tuple = ('a', 'p', 'p', 'l', 'e',)

# In operation
print('a' in my_tuple)
print('b' in my_tuple)

# Not in operation
print('g' not in my_tuple)
```

### Sort tuple
- `sorted()`
- not `.sort()`


```python
my_tuple = ('a', 'p', 'p', 'l', 'e',)
my_tuple.sort()
my_tuple
```


    ---------------------------------------------------------------------------

    AttributeError                            Traceback (most recent call last)

    <ipython-input-17-511c62978fde> in <module>
          1 my_tuple = ('a', 'p', 'p', 'l', 'e',)
    ----> 2 my_tuple.sort()
          3 my_tuple


    AttributeError: 'tuple' object has no attribute 'sort'



```python
my_tuple = sorted(my_tuple)
my_tuple
```




    ['a', 'e', 'l', 'p', 'p']




```python
tup = (8,4)
tupl = tuple(sorted(tup))
tupl
```




    (4, 8)



## Reverse tuple


```python

"""
aTuple = (10, 20, 30, 40, 50)
"""
aTuple = (10, 20, 30, 40, 50)

bTuple = sorted(aTuple, reverse=True)
print(bTuple)
```

    [50, 40, 30, 20, 10]



```python
cTuple = sorted(aTuple, key=lambda x:-x)
print(cTuple)
```

    [50, 40, 30, 20, 10]


Access value 20 from the following tuple


```python
aTuple = ("Orange", [10, 20, 30], (5, 15, 25))
print(aTuple[1][1])
```

    20


Create a tuple with single item 50


```python
aTuple = (50)
print(aTuple)

bTuple = (50,)
print(bTuple)
```

    50
    (50,)


## Unpack the following tuple into 4 variables


```python
aTuple = (10, 20, 30, 40)
a,b,c,d = aTuple
for var in [a,b,c,d]:
    print(var)
```

    10
    20
    30
    40


## Swap the following two tuples


```python
tuple1 = (11, 22)
tuple2 = (99, 88)
print(tuple1, tuple2)

tuple1, tuple2 = tuple2, tuple1
print(tuple1, tuple2)
```

    (11, 22) (99, 88)
    (99, 88) (11, 22)


Copy element 44 and 55 from the following tuple into a new tuple


```python
tuple1 = (11, 22, 33, 44, 55, 66)
tuple2 = (tuple1[-2], tuple1[-1])
print(tuple2)
```

    (55, 66)


Modify the first item (22) of a list inside a following tuple to 222


```python
tuple1 = (11, [22, 33], 44, 55)
tuple1[1][0] = 222
print(tuple1)
```

    (11, [222, 33], 44, 55)


## Sort a tuple of tuples by 2nd item


```python
tuple1 = (('a', 23),('b', 37),('c', 11), ('d',29))
tuple2 = sorted(tuple1, key = lambda x:x[1])
print(tuple2)
```

    [('c', 11), ('a', 23), ('d', 29), ('b', 37)]


Counts the number of occurrences of item 50 from a tuple


```python
tuple1 = (50, 10, 60, 70, 50)
counter = 0
for num in tuple1:
    if num == 50:
        counter+=1
print(counter)
```

    2



```python
from collections import Counter

tuple1 = (50, 10, 60, 70, 50)
counter = Counter(tuple1)
print(counter[50])

```

    2



```python
tuple1 = (50, 10, 60, 70, 50)
print(tuple1.count(50))
```

    2


## Check if all items in the following tuple are the same


```python
tuple1 = (45, 45, 45, 50)
pivot = tuple1[0]

for elem in tuple1:
    if elem != pivot:
        print('No')
else:
    print('Yes')

```

    No
    Yes



```python
all?

"""
Signature: all(iterable, /)
Docstring:
Return True if bool(x) is True for all values x in the iterable.

If the iterable is empty, return True.
Type:      builtin_function_or_method
"""
```


```python
def check(sampleTuple):
    return all(i == sampleTuple[0] for i in sampleTuple)

tuple1 = (45, 45, 45, 45)
print(check(tuple1))
```


```python









```

# String


```python
# Given a string of odd length greater 7, 
# return a string made of the middle three chars of a given String

def getMiddleThreeChars(string):
    mid = len(string)//2
    print(string[mid-1:mid+2])

getMiddleThreeChars("JhonDipPeta")
getMiddleThreeChars("Jasonay")
```

    Dip
    son



```python
# Given 2 strings, s1 and s2, 
# create a new string by appending s2 in the middle of s1

def appendMiddle(s1, s2):
    middleIndex = int(len(s1) /2)
    print("Original Strings are", s1, s2)
    middleThree = s1[:middleIndex-1:]+ s2 +s1[middleIndex-1:]
    print("After appending new string in middle", middleThree)

s = "IamNewString"
appendMiddle("Chrisdem", s)
```

    Original Strings are Chrisdem IamNewString
    After appending new string in middle ChrIamNewStringisdem



```python
# Given 2 strings, s1, and s2 return a new string made of the first, middle and last char each input string

def mixString(s1, s2):
    return s1[0]+s2[0]+s1[-1]+s2[-1]

res = mixString("America", "Japan")
print(res)
```

    AJan



```python
# arrange String characters such that lowercase letters should come first
from collections import deque

def popLowerCases(words):
    lower, upper = [], []
    for ch in words:
        if ch.islower():
            lower.append(ch)
        else:
            upper.append(ch)
       
    return "".join(lower+upper)

input_String = "PyNaTive" # expected: aeiNPTvy
res = popLowerCases(input_String) 
print(res) # list to string, using .join()
```

    yaivePNT



```python
# Given a string input Count all lower case, upper case, digits, and special symbols

def countCharacters(s):
    chars, digits, symbols = 0, 0, 0
    for ch in s:
        if ch.isdigit(): # or ch.isnumeric()
            digits += 1
        elif ch.isalpha(): # or ch.islower() or ch.isupper()
            chars += 1
        else:
            symbols += 1
    return chars, digits, symbols

input_str = "P@#yn26at^&i5ve"
print(countCharacters(input_str))
```

    (8, 3, 4)



```python
# String characters balance Test

def stringBalanceCheck(s1, s2):
    if s1 in s2:
        return True
    else:
        return False
    
# def stringBalanceCheck(s1, s2):
#     flag = True
#     for char in s1:
#         if char in s2:
#             continue
#         else:
#             flag = False
#     return flag

res = stringBalanceCheck("elx", "hello")
print(res)
```

    False



```python
# Find all occurrences of “USA” in given string ignoring the case

input_str = "Welcome to USA. usa awesome, isn't it?"

def countOccurrence(words, pattern):
    low_words = words.lower()
    return low_words.count(pattern.lower())

s = "Welcome to USA. usa awesome, isn't it?"
t = "USA"
res = countOccurrence(s, t)
print(res)
```

    2



```python
# Given an input string, count occurrences of all characters within a string
from collections import Counter

def countAllChars(words):
    count = Counter(words)
    return count

input = "pynativepynvepynative"
res = countAllChars(input)
print(res)
```

    Counter({'p': 3, 'y': 3, 'n': 3, 'v': 3, 'e': 3, 'a': 2, 't': 2, 'i': 2})


Good quiz for string
https://pynative.com/python-string-quiz/


```python
print("John" > "Jhon")
print("Emma" < "Emm")

# explanation
print("germany" > "Germany") # the Unicode value of ‘g’ is greater than the Unicode value of ‘G’

name1 = "Davante" # The Unicode value of ‘a’ is 97 and of ‘e’ is 101. Therefore, “Davante” is smaller than “Dave”.
name2 = "Dave"
print(name1 < name2) 
```

    True
    False
    True
    True



```python
#  get the character from ASCII number

num = 98
print(chr(num))
```

    b



```python
str = "my name is James bond";
print (str.capitalize())
```

    My name is james bond



```python
str = "My salary is 7000";
print(str.isalnum())
```

    False



```python
myString = "pynative"
stringList = ["abc", "pynative", "xyz"]

print(stringList[1] == myString)
print(stringList[1] is myString)
```

    True
    True



```python
strOne = str("pynative")
strTwo = "pynative"
print(strOne == strTwo)
print(strOne is strTwo)
```

    True
    True



```python
str1 = "My salary is 7000";
str2 = "7000"

print(str1.isdigit())
print(str2.isdigit())
```

    False
    True


# regular expression


```python
import re
```


```python
pattern = '^a...s$'
test_string = 'abyss'
result = re.match(pattern, test_string)

if result:
  print("Search successful.")
else:
  print("Search unsuccessful.")	
```

    Search successful.



```python
# re.findall()


# Program to extract numbers from a string

import re

string = 'hello 12 hi 89. Howdy 34'
pattern = '\d+'

result = re.findall(pattern, string) 
print(result)

# Output: ['12', '89', '34']
```

    ['12', '89', '34']



```python
# re.split()

string = 'Twelve:12 Eighty nine:89.'
pattern = '\d+'

result = re.split(pattern, string) 
print(result)
```

    ['Twelve:', ' Eighty nine:', '.']



```python
# re.sub(pattern, replace, string)
# The method returns a string where matched occurrences are replaced with the content of replace variable.

# 找到match的地方，然后用一个string替换掉

# Program to remove all whitespaces
import re

# multiline string
string = 'abc 12\
de 23 \n f45 6'

# matches all whitespace characters
pattern = '\s+'

# empty string
replace = ''

new_string = re.sub(pattern, replace, string) 
print(new_string)

# Output: abc12de23f456
```

    abc12de23f456



```python
# re.search()

# The re.search() method takes two arguments: a pattern and a string. The method looks for the first location where the RegEx pattern produces a match with the string.

string = "Python is fun"

# check if 'Python' is at the beginning
match = re.search('\APython', string)

if match:
  print("pattern found inside the string")
else:
  print("pattern not found")  
```

    pattern found inside the string



```python

```
