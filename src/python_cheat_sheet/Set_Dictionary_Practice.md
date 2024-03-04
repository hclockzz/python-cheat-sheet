# Topics:
- Set
- Dictionary
    - Sorting
    - Convert list to dictionary
- defaultdict
- Counter
- OrderedDict



```python

```

# Set

## Basic operations

Define a set
```Python
x = set(<iter>)
x = {<obj>, <obj>, ..., <obj>}

# set cannot have duplicates
# Output: {1, 2, 3, 4}
my_set = {1, 2, 3, 4, 3, 2}
print(my_set)

# we can make set from a list
# Output: {1, 2, 3}
my_set = set([1, 2, 3, 2])
print(my_set)

# set cannot have mutable items
# here [3, 4] is a mutable list
# this will cause an error.

my_set = {1, 2, [3, 4]}
```

Creating an empty set is a bit tricky.

Empty curly braces {} will make an empty dictionary in Python. To make a set without any elements, we use the set() function without any argument.

### Modifying a set in Python

We can add a single element using the add() method, and multiple elements using the update() method. The update() method can take tuples, lists, strings or other sets as its argument. In all cases, duplicates are avoided.


x.add
```Python
>>> x = {'foo', 'bar', 'baz'}

>>> x.add('qux')
>>> x
{'bar', 'baz', 'foo', 'qux'}
```

x.remove(<elem>)
```Python
>>> x = {'foo', 'bar', 'baz'}

>>> x.remove('baz')
>>> x
{'bar', 'foo'}

>>> x.remove('qux')
Traceback (most recent call last):
  File "<pyshell#58>", line 1, in <module>
    x.remove('qux')
KeyError: 'qux'
```

x.update()
```Python
# add multiple elements
# Output: {1, 2, 3, 4}
my_set.update([2, 3, 4])
print(my_set)

# add list and set
# Output: {1, 2, 3, 4, 5, 6, 8}
my_set.update([4, 5], {1, 6, 8})
print(my_set)
```

x.discard(<elem>)
```Python
>>> x = {'foo', 'bar', 'baz'}
>>> x.discard('baz')
>>> x
{'bar', 'foo'}
>>> x.discard('qux')
>>> x
{'bar', 'foo'}
```

x.pop() Removes a random element from a set.
```Python
>>> x = {'foo', 'bar', 'baz'}

>>> x.pop()
'bar'
>>> x
{'baz', 'foo'}

>>> x.pop()
'baz'
>>> x
{'foo'}

>>> x.pop()
'foo'
>>> x
set()

>>> x.pop()
Traceback (most recent call last):
  File "<pyshell#82>", line 1, in <module>
    x.pop()
KeyError: 'pop from an empty set'
```



## Advanced operation

union of two sets
```Python

>>> x1 = {'foo', 'bar', 'baz'}
>>> x2 = {'baz', 'qux', 'quux'}

>>> x1.union(x2)
{'foo', 'qux', 'quux', 'baz', 'bar'}

>>> x1 | x2
{'foo', 'qux', 'quux', 'baz', 'bar'}

>>> a = {1, 2, 3, 4}
>>> b = {2, 3, 4, 5}
>>> c = {3, 4, 5, 6}
>>> d = {4, 5, 6, 7}

>>> a.union(b, c, d)
{1, 2, 3, 4, 5, 6, 7}

>>> a | b | c | d
{1, 2, 3, 4, 5, 6, 7}
```

intersection of two sets
```Python
>>> x2 = {'baz', 'qux', 'quux'}

>>> x1.intersection(x2)
{'baz'}

>>> x1 & x2
{'baz'}

>>> a = {1, 2, 3, 4}
>>> b = {2, 3, 4, 5}
>>> c = {3, 4, 5, 6}
>>> d = {4, 5, 6, 7}

>>> a.intersection(b, c, d)
{4}

>>> a & b & c & d
{4}
```

Difference between two sets
```Python
>>> x1 = {'foo', 'bar', 'baz'}
>>> x2 = {'baz', 'qux', 'quux'}

>>> x1.difference(x2)
{'foo', 'bar'}

>>> x1 - x2
{'foo', 'bar'}

>>> a = {1, 2, 3, 30, 300}
>>> b = {10, 20, 30, 40}
>>> c = {100, 200, 300, 400}

>>> a.difference(b, c)
{1, 2, 3}

>>> a - b - c
{1, 2, 3}
```

Symmetric difference between two sets
```Python
>>> x1 = {'foo', 'bar', 'baz'}
>>> x2 = {'baz', 'qux', 'quux'}

>>> x1.symmetric_difference(x2)
{'foo', 'qux', 'quux', 'bar'}

>>> x1 ^ x2
{'foo', 'qux', 'quux', 'bar'}

>>> a = {1, 2, 3, 4, 5}
>>> b = {10, 2, 3, 4, 50}
>>> c = {1, 50, 100}

>>> a ^ b ^ c
{100, 5, 10}

```

Other operations:
- `x1.isdisjoint(x2)` Determines whether or not two sets have any elements in common.
- `x1.issubset(x2)` or `x1 <= x2` Determine whether one set is a subset of the other.
- `x1 < x2` Determines whether one set is a proper subset of the other.
- `x1.issuperset(x2)` or `x1 >= x2` Determine whether one set is a superset of the other.


```python
x = set(['foo', 'bar', 'baz', 'foo', 'qux'])
print(x)

y = {'foo', 'bar', 'baz', 'foo', 'qux'}
print(y)
```

    {'foo', 'qux', 'baz', 'bar'}
    {'foo', 'qux', 'baz', 'bar'}



```python
y.add('foo')
print(y)

y.add('pin')
print(y)
```

    {'foo', 'qux', 'baz', 'bar'}
    {'baz', 'bar', 'foo', 'qux', 'pin'}


# Set Exercise

Reference:
https://www.programiz.com/python-programming/set
https://pynative.com/python-set-exercise-with-solutions/

 Add a list of elements to a given set


```python
import time
sampleSet = {"Yellow", "Orange", "Black"}
sampleList = ["Blue", "Green", "Red"]

start_time = time.time()
# your code

for elem in sampleList:
    sampleSet.add(elem)
print(sampleSet)
elapsed_time = time.time() - start_time
elapsed_time
```

    {'Red', 'Orange', 'Blue', 'Yellow', 'Black', 'Green'}





    0.00035309791564941406




```python
start_time = time.time()
# your code

sampleSet = sampleSet | set(sampleList)
print(sampleSet)
elapsed_time = time.time() - start_time
elapsed_time
```

    {'Red', 'Blue', 'Orange', 'Yellow', 'Black', 'Green'}





    0.00038695335388183594




```python
start_time = time.time()
# your code

sampleSet.update(sampleList)
elapsed_time = time.time() - start_time
elapsed_time
```




    7.200241088867188e-05



Return a set of identical items from a given two Python set


```python
import time
set1 = {10, 20, 30, 40, 50}
set2 = {30, 40, 50, 60, 70}

start_time = time.time()
set3 = set1.intersection(set2)
print(set3)
elapsed_time = time.time() - start_time
elapsed_time
```

    {40, 50, 30}





    0.00031304359436035156




```python
set1 = [10, 20, 30, 40, 50]
set2 = [30, 40, 50, 60, 70]

set3 = set(set1) & set(set2)
print(set3)

set3 = set(set1) & set(set2)
print(set3)
```

    {40, 50, 30}


Returns a new set with all items from both sets by removing duplicates


```python
set1 = {10, 20, 30, 40, 50}
set2 = {30, 40, 50, 60, 70}

set3 = set1.union(set2)
print(set3)
```

    {70, 40, 10, 50, 20, 60, 30}


Given two Python sets, update first set with items that exist only in the first set and not in the second set.


```python
set1 = {10, 20, 30}
set2 = {20, 40, 50}

set3 = set1.difference(set2)
print(set3)
```

    {10, 30}


Remove 10, 20, 30 elements from a following set at once


```python
set1 = {10, 20, 30, 40, 50}

set1.remove(10)
print(set1)
```

    {40, 50, 20, 30}



```python
set1 = {10, 20, 30, 40, 50}

set1.difference_update({10, 20, 30})
print(set1)
```

    {40, 50}


Return a set of all elements in either A or B, but not both


```python
set1 = {10, 20, 30, 40, 50}
set2 = {30, 40, 50, 60, 70}

print(set1.symmetric_difference(set2))
```

    {20, 70, 10, 60}


Determines whether or not the following two sets have any elements in common. If yes display the common elements


```python
set1 = {10, 20, 30, 40, 50}
set2 = {60, 70, 80, 90, 10}

if set1.intersection(set2):
    print('Yes')
else:
    print('No')
```

    Yes



```python
set1 = {10, 20, 30, 40, 50}
set2 = {60, 70, 80, 90}

if set1.intersection(set2):
    print('Yes')
else:
    print('No')
```

    No


Update set1 by adding items from set2, except common items


```python
set1 = {10, 20, 30, 40, 50}
set2 = {30, 40, 50, 60, 70}

print(set1.union(set2))
```

    {70, 40, 10, 50, 20, 60, 30}



```python
set1.symmetric_difference_update(set2)
print(set1)
```

    {70, 10, 20, 60}


Remove items from set1 that are not common to both set1 and set2


```python
set1 = {10, 20, 30, 40, 50}
set2 = {30, 40, 50, 60, 70}
set1.difference_update(set2)
print(set1)
```

    {10, 20}



```python
set1 = {10, 20, 30, 40, 50}
set2 = {30, 40, 50, 60, 70}
set1.intersection_update(set2)
print(set1)
```

    {40, 50, 30}


### Equality relationship between two sets


```python
import time
set1 = {10, 20, 30, 40, 50}
set2 = {10, 20, 30, 40, 50}

start_time = time.time()
if set1 == set2:
    print('Yes')
else:
    print('No')
elapsed_time = time.time() - start_time
elapsed_time 
```

    Yes





    0.002977132797241211



# Dictionary

## the behavior of having a key in dictionary


```python
dic = {'a':1,'b':1}
if dic['a']:
    print('a in dic')
try:
    if dic['c']:
        print('c in dic')
except:
    print('c not in dic')
```

    a in dic
    c not in dic



```python
color_mapping = {1:[], 2:[], 3:[], 4:[]}
color_mapping

print(color_mapping.values())
```

    dict_values([[], [], [], []])


### Check if Key Exists

```Python
thisdict = {
  "brand": "Ford",
  "model": "Mustang",
  "year": 1964
}
if "model" in thisdict:
  print("Yes, 'model' is one of the keys in the thisdict dictionary")
```

### Dictionary Length
```Python
print(len(thisdict))
```

### key, value, items()
```Python
for x in thisdict.values():
    print(x)

for x, y in thisdict.items():
    print(x, y)
    
```

### iterate over a dictionary
By default iterate on keys
```Python
dct = {"a":12, "k":9, "p":23}
for k in dct:
    print(dct[k])

>> 12, 9, 23
```

### keys()
```Python
car = {
  "brand": "Ford",
  "model": "Mustang",
  "year": 1964
}

x = car.keys()

print(x)
```

### fromkeys
Create a dictionary with 3 keys, all with the value 0:

```Python
x = ('key1', 'key2', 'key3')
y = 0

thisdict = dict.fromkeys(x, y)

print(thisdict)
```

### update key and keep the value
```Python
# two steps
dictionary[new_key] = dictionary[old_key]
del dictionary[old_key]

# one step
dictionary[new_key] = dictionary.pop(old_key)

```



## Basic Operations

### Add items
```Python
thisdict = {
  "brand": "Ford",
  "model": "Mustang",
  "year": 1964
}
thisdict["color"] = "red"
print(thisdict)
```

### Removing Items
```Python
thisdict = {
  "brand": "Ford",
  "model": "Mustang",
  "year": 1964
}
thisdict.pop("model")
print(thisdict)


thisdict = {
  "brand": "Ford",
  "model": "Mustang",
  "year": 1964
}
thisdict.popitem()
print(thisdict)


thisdict = {
  "brand": "Ford",
  "model": "Mustang",
  "year": 1964
}
del thisdict["model"]
print(thisdict)


# delete the whole dict
thisdict = {
  "brand": "Ford",
  "model": "Mustang",
  "year": 1964
}
del thisdict
print(thisdict) #this will cause an error because "thisdict" no longer exists.


# empty the dict
thisdict = {
  "brand": "Ford",
  "model": "Mustang",
  "year": 1964
}
thisdict.clear()
print(thisdict)
```

d.update(<obj>)
> Merges a dictionary with another dictionary or with an iterable of key-value pairs.
    
If <obj> is a dictionary, d.update(<obj>) merges the entries from <obj> into d. For each key in <obj>:

If the key is not present in d, the key-value pair from <obj> is added to d.
If the key is already present in d, the corresponding value in d for that key is updated to the value from <obj>.

```Python
>>> d1 = {'a': 10, 'b': 20, 'c': 30}
>>> d2 = {'b': 200, 'd': 400}

>>> d1.update(d2)
>>> d1
{'a': 10, 'b': 200, 'c': 30, 'd': 400}
```
In this example, key 'b' already exists in d1, so its value is updated to 200, the value for that key from d2. However, there is no key 'd' in d1, so that key-value pair is added from d2.

<obj> may also be a sequence of key-value pairs, similar to when the dict() function is used to define a dictionary.
    
```Python
>>> d1 = {'a': 10, 'b': 20, 'c': 30}
>>> d1.update([('b', 200), ('d', 400)])
>>> d1
{'a': 10, 'b': 200, 'c': 30, 'd': 400}
```

### Copy a Dictionary
You cannot copy a dictionary simply by typing dict2 = dict1, because: dict2 will only be a reference to dict1, and changes made in dict1 will automatically also be made in dict2.

There are ways to make a copy, one way is to use the built-in Dictionary method copy().
```Python
thisdict = {
  "brand": "Ford",
  "model": "Mustang",
  "year": 1964
}
mydict = thisdict.copy()
print(mydict)
```
Another way to make a copy is to use the built-in function dict().


```Python
thisdict = {
  "brand": "Ford",
  "model": "Mustang",
  "year": 1964
}
mydict = dict(thisdict)
print(mydict)
```

### check if dict1 is equal to dict 2

can use `==` to do equal check

```
>>> d1 = {'a': 1, 'b': 2}
>>> d2 = {'b': 2, 'a': 1}
>>> d1 == d2
True
>>> d1 = {'a': [1,2,3], 'b': 2}
>>> d2 = {'b': 2, 'a': [1,2,3]}
>>> d1 == d2
True
```

but `==` does work for the dictionary `.values()`
see https://discuss.python.org/t/equivalence-of-python-dict-values/14834/6


some alternative way is using `deepdiff`
see https://miguendes.me/the-best-way-to-compare-two-dictionaries-in-python

## Advanced operations on dictionary


### Access dictionary with index like list


```python
my_dict = {'foo': 'bar', 'spam': 'eggs'}
next(iter(my_dict)) # outputs 'foo'
```


```python
list(my_dict)[0]
```

Diff between two dictionary


```python
# difference between two dictionary

dict1 = {}
dict1['i'] = 56       
dict1['a'] = 18 
dict1['b'] = 24

dict2 = {}
dict2['i'] = 56       
dict2['a'] = 18 
dict2['b'] = 24

print(dict1-dict2)

dict2['b'] = 30
print(dict1-dict2)

dict2['c'] = 24
print(dict1-dict2)
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-16-b46fe39c68db> in <module>
          9 dict2['b'] = 24
         10 
    ---> 11 print(dict1-dict2)
         12 
         13 dict2['b'] = 30


    TypeError: unsupported operand type(s) for -: 'dict' and 'dict'



```python
from collections import Counter

dict1 = Counter(list('abbad'))

dict2 = Counter(list('abbad'))

print(dict1)
print(dict2)
print(dict1-dict2)

dict2['b'] = 1
print(dict1-dict2)

dict2['c'] = 1
print(dict1-dict2)
print(dict2-dict1)
```

    Counter({'a': 2, 'b': 2, 'd': 1})
    Counter({'a': 2, 'b': 2, 'd': 1})
    Counter()
    Counter({'b': 1})
    Counter({'b': 1})
    Counter({'c': 1})


# Sort dictionary
key Parameter in Python sorted() function
Based on the returned value of the key function, you can sort the given iterable.
`sorted(iterable, key=len)`



```python
# take the second element for sort
def take_second(elem):
    return elem[1]

# random list
random = [(2, 2), (3, 4), (4, 1), (1, 3)]

# sort list with key
sorted_list = sorted(random, key=take_second)

# print list
print('Sorted list:', sorted_list)
```

    Sorted list: [(4, 1), (2, 2), (1, 3), (3, 4)]


### [Sorting with multiple keys](https://www.programiz.com/python-programming/methods/built-in/sorted)

```Python
# Nested list of student's info in a Science Olympiad
# List elements: (Student's Name, Marks out of 100, Age)

participant_list = [
    ('Alison', 50, 18),
    ('Terence', 75, 12),
    ('David', 75, 20),
    ('Jimmy', 90, 22),
    ('John', 45, 12)
]
```
We want to sort the list in such a way that the student with the highest marks is in the beginning. In case the students have equal marks, they must be sorted so that the younger participant comes first.

We can achieve this type of sorting with multiple keys by returning **tuple** instead of a number.

*Two tuples can be compared* by comparing their elements starting from first. If there is a tie (elements are equal), the second element is compared, and so on.
把tuple用在比较上
```Python
>>> (1,3) > (1, 4)
False
>>> (1, 4) < (2,2)
True
>>> (1, 4, 1) < (2, 1)
True
```
Let's use this logic to build our sorting logic.

```Python
participant_list = [
    ('Alison', 50, 18),
    ('Terence', 75, 12),
    ('David', 75, 20),
    ('Jimmy', 90, 22),
    ('John', 45, 12)
]


def sorter(item):
    # Since highest marks first, least error = most marks
    error = 100 - item[1]
    age = item[2]
    return (error, age)


sorted_list = sorted(participant_list, key=sorter)
print(sorted_list)
```

Using Lambda
```Python
participant_list = [
    ('Alison', 50, 18),
    ('Terence', 75, 12),
    ('David', 75, 20),
    ('Jimmy', 90, 22),
    ('John', 45, 12)
]

sorted_list = sorted(participant_list, key=lambda item: (100-item[1], item[2]))
print(sorted_list)
```


```python
"""
Sorting the Keys and Values in alphabetical using the value
"""

# Declaring hash function       
key_value ={}     

# Initializing the value  
key_value['i'] = 56       
key_value['io'] = 56 
key_value['a'] = 18 
key_value['b'] = 24
key_value['ab'] = 18      
key_value['af'] = 18 

print(sorted(key_value.items(), key=lambda kv: (kv[1], kv[0])))
# print(sorted(key_value.items(), key = lambda kv:(kv[1], kv[0]), reverse=True)) 
print([v[0] for v in sorted(key_value.items(), key=lambda kv: (-kv[1], kv[0]))])


```

    [('a', 18), ('ab', 18), ('af', 18), ('b', 24), ('i', 56), ('io', 56)]
    ['i', 'io', 'b', 'a', 'ab', 'af']



```python
# COMPARISON
# reference:
# https://stackoverflow.com/questions/9919342/sorting-a-dictionary-by-value-then-key

key_value['i'] = 56 
key_value['e'] = 56  
key_value['io'] = 56 
key_value['a'] = 18 
key_value['b'] = 24
key_value['ab'] = 18      
key_value['af'] = 18 

print(sorted(key_value.items(), key=lambda kv: (-kv[1], kv[0])))
```

    [('e', 56), ('i', 56), ('io', 56), ('b', 24), ('a', 18), ('ab', 18), ('af', 18)]



```python
key_value['i'] = 56 
key_value['e'] = 56  
key_value['io'] = 56 
key_value['a'] = 18 
key_value['b'] = 24
key_value['ab'] = 18      
key_value['af'] = 18 

print(sorted(key_value.items(), key=lambda kv: (kv[0], kv[1])))
```

    [('a', 18), ('ab', 18), ('af', 18), ('b', 24), ('e', 56), ('i', 56), ('io', 56)]



```python
"""
Sort the dictionary by key
Note:it will sort in lexicogrphical order
"""

from collections import OrderedDict 
  
dict = {'ravi':'10','rajnish':'9','sanjeev':'15','yash':'2','suraj':'32'} 
dict1 = OrderedDict(sorted(dict.items())) 
print(dict1) 
```

    OrderedDict([('rajnish', '9'), ('ravi', '10'), ('sanjeev', '15'), ('suraj', '32'), ('yash', '2')])



```python
"""
dictionary may not be able to be sliced
"""

key_value[:3]
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-5-8a970a79ebca> in <module>
          3 """
          4 
    ----> 5 key_value[:3]
    

    TypeError: unhashable type: 'slice'


# [Conversion from list to dic](https://appdividend.com/2019/11/12/how-to-convert-python-list-to-dictionary-example/)

- Convert the given list to dictionary such that all the odd elements have the key, and even number elements have the value. 
- Convert a List to Dictionary with the same values.
- Convert two lists to dictionary.
- Convert a list of tuples to the dictionary.


```python
# We can convert a list to dict using list comprehension and make a key: value pair of consecutive elements. 
# Finally, typecast the list to dict type.

def listToDict(lst):
    op = {lst[i]: lst[i + 1] for i in range(0, len(lst), 2)}
    return op


lst = ['m', 1, 'b', 2, 'k', 3]
print(listToDict(lst))
```

    {'m': 1, 'b': 2, 'k': 3}



```python
# create a dictionary with all elements in this list as keys
# Each key’s value will be the same, for example. 0

def listToDict(lst):
    op = { i : 0 for i in lst }
    return op


lst = ['millie', 'caleb', 'finn', 'sadie', 'noah']
print(listToDict(lst))
```

    {'millie': 0, 'caleb': 0, 'finn': 0, 'sadie': 0, 'noah': 0}


Python Dictionary **fromKeys()** method creates a new dictionary from a given sequence of elements with a value provided by a user.

creating the dictionary from the list, so Python Dict *fromKeys()* can get the key values from the Python *List* and then convert it to the dictionary keys. We pass the second parameter as 5, which is value, so we get the same output as the above program.


```python
def listToDict(lst):
    op = dict.fromkeys(lst , 5)
    return op


lst = ['millie', 'caleb', 'finn', 'sadie', 'noah']
print(listToDict(lst))
```

    {'millie': 5, 'caleb': 5, 'finn': 5, 'sadie': 5, 'noah': 5}



```python
# What if lst has duplicates

def listToDict(lst):
    op = dict.fromkeys(lst , 1)
    return op

 
lst = ['millie', 'caleb', 'finn', 'sadie', 'noah', 'finn'] # ignore duplicated 'finn'
print(listToDict(lst))
```

    {'millie': 1, 'caleb': 1, 'finn': 1, 'sadie': 1, 'noah': 1}



```python
# creating a dictionary with indexed keys, and values are python list items using dictionary comprehension.

def listToDict(lst):
    op = { i : lst[i] for i in range(0, len(lst) ) }
    return op


lst = ['millie', 'caleb', 'finn', 'sadie', 'noah']
print(listToDict(lst))
```

    {0: 'millie', 1: 'caleb', 2: 'finn', 3: 'sadie', 4: 'noah'}


### How to convert two lists to dictionary


```python
def listToDict(lstA, lstB):
    zippedLst = zip(lstA, lstB)
    op = dict(zippedLst)
    return op


lstStr = ['millie', 'caleb', 'finn', 'sadie', 'noah']
lstInt = [11, 21, 19, 29, 46]
print(listToDict(lstStr, lstInt))
```

    {'millie': 11, 'caleb': 21, 'finn': 19, 'sadie': 29, 'noah': 46}


### Convert the list of tuples to dictionary in Python


```python
def listToDict(lstTup):
    op = dict(lstTup)
    return op


lstTuple = [('millie', 11), ('caleb', 21),
            ('finn', 19), ('sadie', 29), ('noah', 46)]
print(listToDict(lstTuple))
```

    {'millie': 11, 'caleb': 21, 'finn': 19, 'sadie': 29, 'noah': 46}


# Collection: The defaultdict

The defaultdict works exactly like a python dictionary, except for it does not throw KeyError when you 
try to access a non-existent key.

Instead, it initializes the key with the element of the data type that you pass as an argument at the creation of defaultdict. The data type is called default_factory.




```python
from collections import defaultdict

nums = defaultdict(int)
nums['one'] = 1
nums['two'] = 2
print(nums['three'])
```

    0



```python
count = defaultdict(int)
names_list = "Mike John Mike Anna Mike John John Mike Mike Britney Smith Anna Smith".split()
for names in names_list:
    count[names] +=1
print(count)
```

    defaultdict(<class 'int'>, {'Mike': 5, 'John': 3, 'Anna': 2, 'Britney': 1, 'Smith': 2})



```python
li = [2,5,5,7]
dic = dict(li)
li_dict = defaultdict(int, li)
li_dict
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-6-25083d190eb8> in <module>
          1 li = [2,5,5,7]
    ----> 2 dic = dict(li)
          3 li_dict = defaultdict(int, li)
          4 li_dict


    TypeError: cannot convert dictionary update sequence element #0 to a sequence



```python
nums = defaultdict(list)
nums['one'] = [1]
nums['two'] = [2,3]
print(nums)
print(nums['three'])
```

    defaultdict(<class 'list'>, {'one': [1], 'two': [2, 3]})
    []


# Collection: Counter 

The Counter() function in collections module takes an iterable or a mapping as the argument and returns a Dictionary. 

In this dictionary, a key is an element in the iterable or the mapping and value is the number of times that element exists in the iterable or the mapping.

https://stackabuse.com/introduction-to-pythons-collections-module/#thecounter


```python
from collections import Counter

li = [1,2,3,4,1,2,6,7,3,8,1]
cnt = Counter(li)
cnt
```




    Counter({1: 3, 2: 2, 3: 2, 4: 1, 6: 1, 7: 1, 8: 1})




```python
cnt[1]
```




    3




```python
print(list(cnt.elements()))
```

    [1, 1, 1, 2, 2, 3, 3, 4, 6, 7, 8]



```python
print(cnt.most_common(2))
```

    [(1, 3), (2, 2)]



```python
cnt = Counter({1:3,2:4})
deduct = {1:1, 2:2}
cnt.subtract(deduct)
print(cnt)
```

    Counter({1: 2, 2: 2})



```python
# sorted()

top_k = [('the', 4), ('ta', 4), ('is', 3), ('sunny', 2), ('day', 1)]
sorted(top_k, key=lambda kv:(-kv[1],kv[0]))
```




    [('ta', 4), ('the', 4), ('is', 3), ('sunny', 2), ('day', 1)]




```python
# sort()

top_k.sort(key=lambda x: x[1])
top_k
```




    [('day', 1), ('sunny', 2), ('is', 3), ('the', 4), ('ta', 4)]




```python
words = ["i", "love", "leetcode", "i", "love", "coding"]
counter_obj = Counter(words)
for k, v in sorted(counter_obj.items(), key=lambda x: (-x[1],x[0])):
    print(k, v)
```

    i 2
    love 2
    coding 1
    leetcode 1



```python
from collections import Counter

dict1 = Counter(list('abbad'))

dict2 = Counter(list('abbad'))

print(dict1)
print(dict2)
print(dict1-dict2)

dict2['b'] = 1
print(dict1-dict2)

dict2['c'] = 1
print(dict1-dict2)
print(dict2-dict1)
```

    Counter({'a': 2, 'b': 2, 'd': 1})
    Counter({'a': 2, 'b': 2, 'd': 1})
    Counter()
    Counter({'b': 1})
    Counter({'b': 1})
    Counter({'c': 1})



```python
dict1['j'] -= 1
print(dict1)
```

    Counter({'a': 2, 'b': 2, 'd': 1, 'j': -1})



```python
dict3 = Counter('jiji')
dict3
```




    Counter({'j': 2, 'i': 2})



## class collections.OrderedDict([items])

```Python
popitem(last=True)

move_to_end(key, last=True)
```


```python
# Sort the dictionary during the creation and print the members of the dictionary in reverse order
from collections import OrderedDict

dict = {'Afghanistan': 93, 'Albania': 355, 'Algeria': 213, 'Andorra': 376, 'Angola': 244}
order_dict = OrderedDict(dict)
print(order_dict)
```

    OrderedDict([('Afghanistan', 93), ('Albania', 355), ('Algeria', 213), ('Andorra', 376), ('Angola', 244)])



```python
kv = order_dict.popitem()
print(kv)
print(order_dict)
order_dict.move_to_end('Algeria')
print(order_dict)
```

    ('Angola', 244)
    OrderedDict([('Afghanistan', 93), ('Albania', 355), ('Algeria', 213), ('Andorra', 376)])
    OrderedDict([('Afghanistan', 93), ('Albania', 355), ('Andorra', 376), ('Algeria', 213)])



```python
order_dict = reversed(order_dict)
for key in order_dict:
    print(key)
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-4-e93648c5300a> in <module>
    ----> 1 order_dict = reversed(order_dict)
          2 for key in order_dict:
          3     print(key)


    TypeError: 'odict_iterator' object is not reversible



```python
order_dict = reversed(order_dict.items()) # reversed() return None
for key in order_dict:
    print(key)
```


    ---------------------------------------------------------------------------

    AttributeError                            Traceback (most recent call last)

    <ipython-input-6-b6fe988e870f> in <module>
          1 # order_dict = reversed(order_dict.items())
    ----> 2 for key in order_dict.items():
          3     print(key)


    AttributeError: 'odict_iterator' object has no attribute 'items'



```python
# creating a simple dict
my_dict = {'kiwi': 4, 'apple': 5, 'cat': 3}

# creating empty ordered dict
ordered_dict = OrderedDict()
print(ordered_dict)

# creating ordered dict from dict
ordered_dict = OrderedDict(my_dict)
print(ordered_dict)
```

    OrderedDict()
    OrderedDict([('kiwi', 4), ('apple', 5), ('cat', 3)])



```python
# pop last item
item = ordered_dict.popitem(True)
print(item)
print(ordered_dict)
```

    ('cat', 3)
    OrderedDict([('kiwi', 4), ('apple', 5)])



```python
# reversed iteration
for item in reversed(ordered_dict):
    print(item)
```

    cat
    apple
    kiwi


### OrderedDict Equality Tests Example


```python
# equality tests
d1 = {'a': 'A', 'b': 'B'}
d2 = {'b': 'B', 'a': 'A'}

od1 = OrderedDict({'a': 'A', 'b': 'B'})
od2 = OrderedDict({'b': 'B', 'a': 'A'})

print(d1 == d2)
print(od1 == od2)
print(d1 == od1)
```

    True
    False
    True



```python









```

# Leetcode Code Challenges


```python
# 1.Two Sum

# my solution

from collections import defaultdict

class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        nums_dict = defaultdict(list)
        
        for i,num in enumerate(nums):
            if not nums_dict[num]:
                nums_dict[num] = [i]
            else:
                nums_dict[num].append(i)
                
        for i,num in enumerate(nums):
            div = target - num
            print("num:{} div:{} nums_dict[div]:{}".format(num, div, nums_dict[div]))
            if nums_dict[div]:
                if div != num:
                    return [i, nums_dict[div][0]]
                if div == num and len(nums_dict[div]) > 1:
                    return nums_dict[div][:2]
        return []
```


```python
# Good solution
"""
for num in nums:
    Put target - num in dictionary
    if num is what you put in dictionary before
        return 
"""

class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        memory = {}
        for i, e in enumerate(nums):
            if e in memory: return (memory[e], i)
            memory[(target - e)] = i
        return []
```


```python
### template: Two Sum


```


```python
nums = [2, 7, 11, 15]
nums = enumerate(nums)
nums = sorted(nums, key=lambda x:x[1])
nums
```




    [(0, 2), (1, 7), (2, 11), (3, 15)]




```python
# two-pointer solution      

def twoSum(self, nums, target):
    nums = enumerate(nums)
    nums = sorted(nums, key=lambda x:x[1])
    l, r = 0, len(nums)-1
    while l < r:
        if nums[l][1]+nums[r][1] == target:
            return sorted([nums[l][0]+1, nums[r][0]+1])
        elif nums[l][1]+nums[r][1] < target:
            l += 1
        else:
            r -= 1
```


```python
# 136. Single Number

class Solution:
    def singleNumber(self, nums: List[int]) -> int:
        return functools.reduce(lambda x, y: x ^ y, nums)
```


```python
8 ^ 2 ^ 2
```




    8




```python

```
