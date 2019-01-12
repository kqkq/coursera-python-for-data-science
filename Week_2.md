# Week 2

## Lists and Tuples

### Tuples

Ordered sequence. Immutable.

```python
>>> tp = ('hello', 12345, 3.1415926) # Different types in a tuple
>>> tp
('hello', 12345, 3.1415926)
>>> type(tp) # Type of the tuple is `tuple`
<class 'tuple'>
>>> tp[0] # Access by index, the index can be negative
'hello'
>>> tp = tp + ('and', ' ', 'more')   # Concatenate
>>> tp
('hello', 12345, 3.1415926, 'and', ' ', 'more')
>>> tp[2:4]  # Slicing
(3.1415926, 'and')
>>> len(tp)  # determine the length
6
>>> tp[1]=666   # Immutable
Traceback (most recent call last):
  File "<pyshell#24>", line 1, in <module>
    tp[1]=666
TypeError: 'tuple' object does not support item assignment
```

#### Sort a tuple

```python
>>> tp1 = (6, 2, 5, 7, 1)
>>> tp1
(6, 2, 5, 7, 1)
>>> type(tp1)
<class 'tuple'>
>>> tp1 = sorted(tp1)
>>> tp1
[1, 2, 5, 6, 7]  # brackets, not parentheses???
>>> type(tp1)
<class 'list'>  # shit!!!
```

Tuples can be nested. A nested tuple behaves like a **tree**.

### Lists

Ordered sequence. Behaves like a tuple, but mutable.

```
>>> l = [3, 6, 2, 1, 7]
>>> l[2] = 999
>>> l
[3, 6, 999, 1, 7]
```

### List manipulation

```python
>>> l = [1, 2]
>>> l = l + [3, 4]  # Concatenate
>>> l
[1, 2, 3, 4]
>>> l.extend([5, 6])  # Extend
>>> l
[1, 2, 3, 4, 5, 6]
>>> l.append([7, 8])  # Append
>>> l
[1, 2, 3, 4, 5, 6, [7, 8]]
>>> del(l[3])         # Delete
>>> l
[1, 2, 3, 5, 6, [7, 8]]
```

### String to List

```python
>>> s = 'hello world'   # Split by space by default
>>> s.split()
['hello', 'world']

>>> s='小了白了兔了白了又了白'
>>> s.split('了')       # Specified delimiter
['小', '白', '兔', '白', '又', '白']
```

### List clone

```python
>>> a = [1,2]
>>> b=a         # b is an alias of a
>>> a[0]=666
>>> b  
[666, 2]

>>> c=a[:]      # c is a clone of a
>>> c[0]=999
>>> c
[999, 2]
>>> a
[666, 2]
```

### Lab: Tuples

Find an element from a tuple:

```
xxx.index(value)
```

Example:

```python
genres_tuple = ("pop", "rock", "soul", "hard rock", "soft rock", "R&B", "progressive rock", "disco")
genres_tuple.index('disco')  # return 7
```

Trap:

```python
genres_tuple.index('not-exist') # Exception raised
```

### Lab: Lists

Too easy ;)

### Quiz

1. Consider the tuple `tuple1=("A","B","C" )`, what is the result of the following operation `tuple1[-1]`?

- [ ] "A"
- [x] "C"
- [ ] "B"

2. Consider the tuple `A=((1,),[2,3],[4])`, that contains a tuple and list. What is the result of the following operation `A[2]`:

- [ ] [2,3]
- [x] [4]
- [ ] 1

3. Consider the tuple `A=((1,),[2,3],[4])`, that contains a tuple and list. What is the result of the following operation `A[2][0]`:

- [x] 4
- [ ] [4]
- [ ] 1

**Note: Consider a tuple `(1,)`. The trailing comma is required. For multiple element tuples like `(1,2,3,)`, the trailing comma is optional.  Reference: https://wiki.python.org/moin/TupleSyntax**

4. What is the result of the following operation: `'A,B,C,D'.split(',')`

- [x] ['A', 'B', 'C', 'D']
- [ ] ('A', 'B', 'C', 'D')
- [ ] 'A,B,C,D'

5. After applying the following method, `L.append(['a','b'])`, the following list will only be one element longer.

- [x] True
- [ ] False

6. What is an important difference between lists and tuples?

- [ ] Lists can't contain a string
- [ ] Tuples can only have integers
- [ ] Lists and tuples are the same
- [x] Lists are mutable tuples are not

7. consider the following list: `A=["hard rock",10,1.2]`
  what will list `A` contain affter the following command is run: `del(A[0])`

- [x] [10,1.2]
- [ ] ["hard rock",10,1.2]
- [ ] ["hard rock",10]

8. if `A` is a list what does the following syntax do: `B=A[:]`

- [ ] assigns list `A` to list `B`
- [x] variable `B` references a new copy or clone of the original list `A`

9. what is the result of the following: `len(("disco",10,1.2, "hard rock",10))`

- [x] 5
- [ ] 6
- [ ] 0

## Dictionaries

A Key-Value data structure.

Key should be a string or any immutable objects.

```python
>>> dict = {'a': 1, 'b': 2}  # Define
>>> dict['a']                # Access
1
>>> 'a' in dict              # Check
True
>>> 'c' in dict
False
>>> dict.keys()              # List all keys
dict_keys(['a', 'b'])
>>> type(dict.keys())
<class 'dict_keys'>          # WTF?
>>> dict.values()            # List all values
dict_values([1, 2])
```

### Note: The order of a Dictionary

**For Python 2**: Keys and values are listed in an **arbitrary order** which is non-random, varies across Python implementations, and depends on the dictionary’s history of insertions and deletions. (Ref: https://docs.python.org/2.7/library/stdtypes.html#dict.items)

**For Python 3**: Dictionaries preserve insertion order. Note that updating a key does not affect the order. Keys added after deletion are inserted at the end. Dictionary order is **guaranteed to be insertion order**. This behavior was an implementation detail of CPython from 3.6. (Ref: https://docs.python.org/3/library/stdtypes.html#dict.values)

### Quiz

1. Consider the following dictionary:

```
{ "The Bodyguard":"1992", "Saturday Night Fever":"1977"}
```

select the values

- [x]  "1977"
- [x]  "1992"
- [ ]  "The Bodyguard"
- [ ] "Saturday Night Fever"

2. The variable `release_year_dict` is a Python Dictionary, what is the result of applying the following method: `release_year_dict.values()`

- [ ] retrieve the keys of the dictionary
- [x] retrieves, the values of the dictionary

3. how many identical keys can a dictionary have

- [x] 0
- [ ] 3
- [ ] 100000000

## Sets

* A collection
* Unordered
* Unique elements

```python
s = {'A', 'B', 'C'}
```

### Type casting from list to set

```
>>> fib = [1, 1, 2, 3, 5, 8]
>>> s = set(fib)
>>> s
{1, 2, 3, 5, 8}
>>> type(s)
<class 'set'>
```

### Set operations

* `add()`
* `remove()`
* element `in` set
* intersect: `set1.intersection(set2)` or `set1 & set2`
* union: `set1.union(set2)`
* subset: `set1.issubset(set2)`
* superset: `set1.issuperset(set2)`
* difference: `set1.difference(set2)`

```python
>>> s.add(13)
>>> s
{1, 2, 3, 5, 8, 13}
>>> s.remove(1)
>>> s
{2, 3, 5, 8, 13}
>>> s & {1, 2, 3}  # Intersect
{2, 3}
>>> s.union({21})  # Union
{2, 3, 5, 21, 8, 13}  # The order is not preserved
>>> {2,3}.issubset(s) # Is subset
>>> s.issuperset({2, 3})
True
```

### Quiz

1. Consider the list `A`, what will be the result of the following operation: `set(A)`

- [ ] the result will be a dictionary
- [x] the result will be a set
- [ ] the result will be a list

2. Consider the Set:`V={'A','B'}`, what is the result of `V.add('C')`?

- [ ] error
- [ ] {'A','B'}
- [x] {'A','B','C'}

3. what is the result of the following:` 'A' in {'A','B'}`

- [ ] False
- [x] True