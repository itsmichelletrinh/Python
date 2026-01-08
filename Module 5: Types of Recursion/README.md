# Module 5 Assignment Questions

## 📚 Table of Contents
- [Instructions](#instructions)
- [Question #1 and Solution](#question-1-and-solution)
- [Question #2 and Solution](#question-2-and-solution)
- [Question #3 and Solution](#question-3-and-solution)

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
Testing must be done using the check module.
When a function produces a floating point value, you must use check.within for your testing. Unless told
otherwise, use a tolerance of 0.00001 in your tests.

Test data for all questions will always meet the stated assumptions for consumed values.
````

- Restrictions
  
````
Do not import any modules other than math and check. You are always allowed to define your own
helper/wrapper functions, as long as they meet the assignment restrictions. Do not use Python constructs
from later modules (e.g., dictionaries, loops (for or while or others), zip, functions with default
parameters, left hand slicing (experessions of the form L[:] = ... where L is a list), sorted, anything
with set or enumerators, ord, chr, try and except).

For this assignment specifically, abstract list functions, map, and filter are not allowed!

Do not mutate passed parameters for required functions unless otherwise told to.

Use only the functions, methods, operations, constants and keywords as follows:

- abs, len, max, min, sum and range (however keyword parameters for these functions are not allowed and
  sum should only consume a single list parameter)
- Any method or constant in the math module
- Any basic arithmetic or comparison operations (+, -, *, /, //, %, **, <, <=, ==, != >, >=)
- Any basic logical operators (not, and, or)
- These typecasting operators: int(), str(), float(), bool(), list(), and type()
- if statements (including elif and else)
- String or list slicing and indexing as well as string or list operations using the operators above 
- The in operator and any string or list methods listed below except for using specified keyword
  parameters key and reverse in the sort method (which will be introduced in module 8)
- input and print as well as the formatting parameter end and method format. Note that all prompts must
  match exactly in order to obtain marks so ensure that you do not alter these prompts.
- Recursion

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

When dealing with elevations, sometimes things are kept track of using changes (or deltas). This may be because barometric altimeters cannot give absolute values (since air pressure changes) but can measure relative changes.

Consider the following hill / mountain:

<img width="745" height="430" alt="image" src="https://github.com/user-attachments/assets/61f65d0e-4d2a-4e8b-b8a8-ac6b0bff6a14" />

We can represent these absolute measurements with the following list of changes: 

````python
[5, -3, 2, 3, -4, -3]
````

**1. Write the function**

````python
alt_max(L)
````
         
**that consumes a list of integers `L` representing the changes, and returns the highest altitute measured (NOT the largest change). Assume we start at height 0.**

**Sample:**

````python
alt_max([5,-3, 2, 3 ,-4 ,-3, -7]) => 7
````

You must use **accumulative recursion** for this question and all recursive functions you write must be accumulative. Solutions using other approaches will receive 0 (ZERO) correctness marks.

Please click on the following link for my [solution](https://github.com/itsmichelletrinh/Python/blob/main/Module%205%3A%20Types%20of%20Recursion/Q1%3A%20Highest%20Altitude.md).

***

## Question #2 and Solution

**2. Write the function**

````python
count_chars(s, chars)
````
         
**that consumes a string `s`, and a second string `chars`. The function returns a list of natural numbers that has the same length as chars.** The number at index `i` in the returned list represents how many of character `chars[i]` occurred in the string `s`. 
Note that values in `chars` may repeat.

**Sample:**

````python
count_chars("Hello, world!  This is a test", "aeiou") => [1, 2, 2, 2, 0]
count_chars("Hello there Number 7", "h") => [1]
````

You must use **accumulative recursion** for this question and each recursive function you write must be accumulative. Solutions using other approaches will receive 0 (ZERO) correctness marks.

Please click on the following link for my [solution](https://github.com/itsmichelletrinh/Python/blob/main/Module%205%3A%20Types%20of%20Recursion/Q2%3A%20Count%20Characters.md).

***

## Question #3 and Solution

On Assignment 3 you converted an octal string into an `Int` value using simple structural recursion.

It's a bit tricky to do this in reverse. It is much easier with more advanced recursive approaches. Perhaps too easy. To make things more complicated, we'll be converting `Int` values to strings in any base.

**3. Write the function**

````python
base_convert(n, s)
````
         
**that consumes a natural number `n`, and a string `s` of 2 or more characters. These characters represent the digits in the desired number system, so they must be unique (but can be any printable character, not only the digits '0' through '9').**

**Examples:**

````python
base_convert(17, "01234567") => "21"
base_convert(17, "abcdefghij") => "bh"
````

**Explanations:**

The first example can be written as 17=2*8+1 and so we get the value 21 from this. The second example is in base 10 but we change the digits to be the letters from '`a`' to '`j`'. See below for another explanation on how to compute these values.

**Hint:** 

This conversion can be tricky if you don't approach it the right way. It is easiest to start with the last digit which is just the remainder when `n` is divided by the number of 'digits' you are using. Then subtract this remainder from `n` and 
divide by the number of 'digits'. Repeat the process to get the second last digit. There are other methods and you are not obligated to use this idea but I recommend trying this approach. Also, it might help to first do at least the above examples by 
hand to get a handle on the algorithm before coding.

Please click on the following link for my [solution](https://github.com/itsmichelletrinh/Python/blob/main/Module%205%3A%20Types%20of%20Recursion/Q3%3A%20Convert%20Integers%20to%20Strings%20in%20Any%20Base.md).

***
