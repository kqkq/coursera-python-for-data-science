# Week 1

## Types

### Python types

* `int`
* `float`
* `str`
* ...

The `type()` command: determine the type

```python
>>> type(123)
<class 'int'>
>>> type(3.14)
<class 'float'>
```

### Type casting

```python
>>> float(2)
2.0
>>> int(3.99)
3   # Like C++
>>> int('123')
123  # Also parse strings!
>>> str(3.14)
'3.14'
```

###  Boolean

Keyword: `bool`, `True` and `False`

```python
>>> type(True)
<class 'bool'>
```

Type casting between `bool` and `int` is just like C++

```python
>>> int(True)
1
>>> int(False)
0
>>> bool(1)
True
>>> bool(0)
False
>>> bool(1234)
True
>>> bool(-1)
True
```

### Quiz

1. what is the type of the following: **1.0**
- [x] float
- [ ] int
- [ ] str

2. what is the result of the following code segment: **type(int(12.3))**

- [x] int
- [ ] float
- [ ] str

3. What is the result of the following code segment: **int(3.99)**
- [x] 3
- [ ] 3.99
- [ ] 4

4. What is the result of the following code segment: int(False)
- [ ] 1
- [x] 0
- [ ] error

## Expressions and Variables

### Expressions

* Operands
* Operators

Python 3: (in term of *true division*)

```python
>>> 25/5
5.0
>>> 25/6
4.166666666666667
```

Python 2: (in term of *floor division*, like C++)

```python
>>> 25/5
5
>>> 25/6
4
```

Reference: https://www.python.org/dev/peps/pep-0238/

Both version:

```python
>>> 15//4
3
```

### Variables

Too boring...

### Quiz

1. What is the result of the following code segment:1/2
- [x] 0.5 (Python 3)
- [x] 0 (Python 2)

2. What is the value of x after the following lines of code:
```python
x=2
x=x+2
```

- [x] 4
- [ ] 2

3. What is the result of the following operation 3+2*2?
- [ ] 3
- [x] 7
- [ ] 9

4. What is the type of the variable x after the following: x=1/1
- [x] float (Python 3: True division **always** return a `float`)
- [x] int  (Python 2: Floor division **always** return an `int`)

## Lab: Types, Expressions and Variables

Most exercises on types, expressions, and variables are too boring. But I found these:

### Check the Python Version

```python
>>> import sys
>>> sys.version
'3.7.2 (tags/v3.7.2:9a3ffc0492, Dec 23 2018, 23:09:28) [MSC v.1916 64 bit (AMD64)]'
```

### Float info

```python
>>> import sys
>>> sys.float_info
sys.float_info(max=1.7976931348623157e+308, max_exp=1024, max_10_exp=308, min=2.2250738585072014e-308, min_exp=-1021, min_10_exp=-307, dig=15, mant_dig=53, epsilon=2.220446049250313e-16, radix=2, rounds=1)
```

Note: The `float` is double precision, like `double` in C/C++.

## Strings

* Single quotes
* Double quotes

Access characters by subscripts (or index) start from 0.

```python
>>> s = 'Kuang'
>>> s[0]   # C-alike strings (char arrays)
'K'
>>> s[4]
'g'
>>> s[5]   # Python will check the range of index, C/C++ will not
Traceback (most recent call last):
  File "<pyshell#34>", line 1, in <module>
    s[5]
IndexError: string index out of range
>>> s[-1]  # Neg. index to access elements backward
'g'
>>> s[-5]
'K'
>>> s[-6] 
Traceback (most recent call last):
  File "<pyshell#40>", line 1, in <module>
    s[-6]
IndexError: string index out of range
```

### Slicing

```python
>>> s = '0123456789'
>>> s[0:4]
'0123'
>>> s[0:100]  # No IndexError, No worries
'0123456789'
>>> s[::2]    # Slice every other char
'02468'
>>> s[0:5:2]
'024'
###############################
>>> s[-10:-5] # Neg. index also works
'01234'
>>> s[-10:5] 
'01234'
###############################
>>> s[::-1]   # Pythonic black magic ;)
'9876543210'
```

Summary:

```
string [ start index (inc.) : end index (excl.) : step length ]
```

### Length

`len()` function

### Concatenate

```
>>> '123'+'456'
'123456'
```

### Replicate

```python
>>> 6*'6'
'666666'
>>> 'Awesome!'*32
'Awesome!Awesome!Awesome!Awesome!Awesome!Awesome!Awesome!Awesome!Awesome!Awesome!Awesome!Awesome!Awesome!Awesome!Awesome!Awesome!Awesome!Awesome!Awesome!Awesome!Awesome!Awesome!Awesome!Awesome!Awesome!Awesome!Awesome!Awesome!Awesome!Awesome!Awesome!Awesome!'
```

### Strings are Immutable (like Java)

```python
>>> s='Kuang'
>>> s[0]
'K'
>>> s[0]='k'
Traceback (most recent call last):
  File "<pyshell#5>", line 1, in <module>
    s[0]='k'
TypeError: 'str' object does not support item assignment
```

### Escaping

Use backslash just like any other language...

```
>>> s1 = '1\n2'
>>> s2 = r'1\n2'
>>> print(s1)
1
2
>>> print(s2)
1\n2
```

When an `'r'` or `'R'` prefix is present, a character following a backslash is included in the string without change, and all backslashes are left in the string. 

### String manipulation

* Sequence methods: work on all lists and tuples
* String methods: work only on strings

String methods:

* `upper()`
* `replace()`
* `find()`


### Quiz

1. In Python, if you executed `name = 'Lizz'`, what would be the output of `print(name[0:2])`?

- [ ] Lizz
- [ ] L
- [x] Li

2. In Python, if you executed `var = '01234567'`, what would be the result of `print(var[::2]).`

- [x] 0246
- [ ] 1357
- [ ] 1234567

3. In Python, what is the result of the following operation: `'1'+'2'`

- [ ] 3
- [ ] '3'
- [x] '12'

4. What is the result of the following: `'hello'.upper()`

- [x] 'HELLO"
- [ ] 'Hello'
- [ ] 'hello'

5. Consider the string `Name="Michael Jackson"` , what is the result of the following operation `Name.find('el')`

- [ ] 1
- [x] 5
- [ ] -1

6. what is the result of the following `str(1)+str(1)`

- [x] '11'
- [ ] 2

7. what is the result of the following: `"123".replace("12", "ab")`

- [x] 'ab3'
- [ ] '123ab'

## Lab: Strings

Solutions were given online.