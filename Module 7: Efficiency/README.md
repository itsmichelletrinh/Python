# Module 7 Assignment Questions

## 📚 Table of Contents
- [Instructions](#instructions)
- [Question #1 and Solution](#question-1-and-solution)
- [Question #2 and Solution](#question-2-and-solution)

Please note that all questions are created by University of Waterloo, School of Computer Science for the CS116: Introduction to Computer Science 2 course.

***

## Instructions
The following instructions were given to students:

- Style Guide

````
- Natural numbers in this course begin at 0.
- Required functions need all design recipe elements. Functions you define (e.g., helper functions) need all
  design recipe elements except for examples and tests.
````

- Testing

````
- Testing must be done using the check module.
- When a function produces a floating point value, you must use check.within for your testing. Unless told
  otherwise, use a tolerance of 0.00001 in your tests.
- Test data for all questions will always meet the stated assumptions for consumed values.
````

- Restrictions
  
````
Do not import any modules other than math and check.  You are always allowed to define your own helper/wrapper
functions, as long as they meet the assignment restrictions. Do not use Python constructs from later modules
(e.g. dictionaries, commands continue or break,zip, functions with default parameters, left hand slicing
(experessions of the form L[:] = ... where L is a list), sorted, anything with set or enumerator, ord, chr,
try and except, list comprehension, etc.).

For this assignment specifically, abstract list functions, map, and filter are not allowed.
Recursion is also prohibited!

Do not mutate passed parameters for required functions unless otherwise told to.

Use only the functions, methods, operations, constants and keywords as follows:

- abs, len, max, min, sum and range (however keyword parameters for these functions are not allowed and sum
  should only consume a single list parameter)
- Any method or constant in the math module
- Any basic arithmetic or comparison operations (+, -, *, /, //, %, **, <, <=, ==, != >, >=)
- Any basic logical operators (not, and, or)
- These typecasting operators: int(), str(), float(), bool(), list(), and type()
- if statements (including elif and else)
- String or list slicing and indexing as well as string or list operations using the operators above
- The in operator and any string or list methods listed below except for using specified keyword parameters key
  and reverse in the sort method (which will be introduced in module 8)
- input and print as well as the formatting parameter end and method format. Note that all prompts must match
  exactly in order to obtain marks, so ensure that you do not alter these prompts.
- Loops, specifically while loops and single variable for loops.

Read each question carefully for additional restrictions.
````

- Additional Notes

````
While you may use global constants in your solutions, do not use global variables for anything other than testing.

The solutions you submit must be entirely your own work. Do not look up either full or partial solutions on the
Internet or in printed sources.

String methods include: ('capitalize', 'casefold', 'center', 'count', 'endswith', 'expandtabs', 'find', 'format',
'index', 'isalnum', 'isalpha', 'isdecimal', 'isdigit', 'isidentifier', 'islower', 'isnumeric', 'isprintable',
'isspace', 'istitle', 'isupper', 'join', 'ljust', 'lower', 'lstrip', 'partition', 'replace', 'rfind', 'rindex',
'rjust', 'rpartition', 'rsplit', 'rstrip', 'split', 'splitlines', 'startswith', 'strip', 'swapcase', 'title',
'upper', 'zfill')

List methods include: ('append', 'clear', 'copy', 'count', 'extend', 'index', 'insert', 'pop', 'remove',
'reverse', 'sort')
````

***

## Question #1 and Solution

Highly repetitive data can sometimes be compressed using something called run-length encoding: It is shorter to write "8o" instead of "oooooooo".

Run-length encoding uses two key ideas:

- a string can be partitioned into blocks (e.g. '`aaabbabbbbb`' can be partitioned into the blocks '`aaa`', '`bb`', '`a`' and '`bbbbb`')
- each block can be represented by a number and one character (e.g. '`aaaaa`' can be represented by '`5a`').

For example, the encoding of "`aaabbabbbbbbbbbbb`" is "`3a 2b 1a 11b`".

Below is a simple decode function:

````python
def rl_decode(s):
  '''
  Decodes a Run Length encoded string s
  
  rl_decode: Str -> Str
  
  Examples:
     rl_decode("") => ""
     rl_decode("3a 2b 1a 11b") => "aaabbabbbbbbbbbbb"
  '''
  return "".join(map(lambda s: int(s[:-1]) * s[-1], s.split()))
````

**1. You must write the inverse function:**

```python
rl_encode(s)
````
         
**that consumes a space-less string `s`, and returns its run length encoding in O(n) time where n is the length of the string `s`.**

**Note (and hint!)**: 

The join method of strings is O(n), where n is the total number of characters in the elements of the list.

**Samples:**

````python
rl_encode("aaabbabbbbbbbbbbb") => "3a 2b 1a 11b"
rl_encode('7') => '7'
rl_encode("aa") => "2a"
````

Please click on the following link for my [solution](https://github.com/itsmichelletrinh/Python/blob/main/Module%207%3A%20Efficiency/Q1%3A%20Run-Length%20Encoding.md).

***

## Question #2 and Solution

**2. Write a function**

````python
moving_average(L, k)
````
         
**that consumes a list of natural numbers `L` and a positive integer `k`, and returns a list of `len(L) - k + 1` floating point numbers corresponding to the moving average as described below. If `k > len(L)` the function returns an empty list. 
Your code must work in O(n) time, not O(n*k).**

In the **moving average**, the first element is the average of `L[:k]` (the first `k` elements of `L`), the second element is the average of `L[1:k+1]` (the first `k` elements starting from index 1). etc. In general, index `i` in the returned list 
will be the average of `L[i, k + i]`.

**Aside:**

The moving average is useful for smoothing out graphs of stock prices or other noisy data.

**Samples:**

````python
moving_average([2183746932, 3912874801], 1) => [2183746932.0, 3912874801.0],
moving_average([20, 18, 13, 16, 25, 22, 9], 2) => [19.0, 15.5, 14.5, 20.5, 23.5, 15.5]
````

**Note:**

When using `check.within` make sure that all of the values in the expected list are `float` values. If you use `19` instead of `19.0` then it will not match.

Please click on the following link for my [solution](https://github.com/itsmichelletrinh/Python/blob/main/Module%207%3A%20Efficiency/Q2%3A%20Moving%20Average.md).

***
