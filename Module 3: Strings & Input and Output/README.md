# Module 3 Assignment Questions

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
- Testing must be done using the check module.
- When a function produces a floating point value, you must use check.within for your testing. Unless told
  otherwise, use a tolerance of 0.00001 in your tests.
- Test data for all questions will always meet the stated assumptions for consumed values.
````

- Restrictions
  
````
Do not import any modules other than math and check. You are always allowed to define your own helper/wrapper
functions, as long as they meet the assignment restrictions. Do not use Python constructs from later modules
(e.g. dictionaries, loops (for or while or others), zip, functions with default parameters, sorted, anything
with sets or enumerators and/or lists, ord, chr, try and except). Use only the functions, methods, operations,
constants and keywords as follows:

- abs, len, max, and min (however keyword parameters for these functions are not allowed)
- Any method or constant in the math module
- Any basic arithmetic or comparison operations (+, -, *, /, //, %, **, <, <=, ==, != >, >=)
- Any basic logical operators (not, and, or)
- These typecasting operators: int(), str(), float(), bool(), and type()
- if statements (including elif and else)
- String slicing and indexing as well as string operations using the operators above.
- String methods: capitalize, count, endswith, find, index, isalnum, isalpha, isdecimal, isdigit, islower,
  isnumeric, isspace, istitle, isupper, lower, lstrip, replace, rfind, rindex, rstrip, startswith, strip,
  swapcase, title, upper, zfill
- The operation in for strings.
- input and print as well as the formatting parameter end and method format. Note that all prompts must match
  exactly in order to obtain marks so ensure that you do not alter these prompts.
- Recursion
````

- Additional Notes

````
- While you may use global constants in your solutions, do not use global variables for anything other
  than testing.
- Read each question carefully for additional restrictions.
- The solutions you submit must be entirely your own work. Do not look up either full or partial solutions
  on the Internet or in printed sources.
````

***

## Question #1 and Solution

You are likely familiar with the base 10 number system, where each digit represents a power of 10. For example, 721 means <img width="221" height="27" alt="image" src="https://github.com/user-attachments/assets/c4821c3a-a736-419c-ae06-4a7518a12aff" />.

This kind of number system works with different bases. Computers sometimes use a base 8 number system, called octal. In octal, 721 would mean <img width="183" height="27" alt="image" src="https://github.com/user-attachments/assets/af5865c7-570b-4c0b-90cc-4b94f5d199ff" />
which is 465 in decimal.

**1. Write the Python function**

````python
octal_to_int(s)
````
         
**that consumes a non-empty string `s` corresponding to a non-negative number in octal, and returns its decimal value as a natural number.**

**Sample:**

````python
octal_to_int("721") => 465
octal_to_int("7") => 7
````

**Hint:** 
````python 
int('3') => 3
````

**Note:** For this problem you are banned from using the built-in function `oct` which does this conversion for you. You are also banned from using the built-in function `int` to do octal conversions. You may use it in decimal conversions as shown in the hint.

Please click on the following link for my [solution](https://github.com/itsmichelletrinh/Python/blob/main/Module%203%3A%20Strings%20%26%20Input%20and%20Output/Q1%3A%20%20Octal%20Number%20to%20Integer.md).

***

## Question #2 and Solution

**1. Write the Python function**

````python
guessing_game(hidden, num_guesses)
````
         
**that consumes two positive integers. The first, `hidden` is the number being guessed, and it must be between 1 and 100 (inclusive). The second, `guessed` is the number of guesses to allow. The function returns `None`.**

The function repeatedly reads a guess from the user. For each guess:

- If the guess is correct, the function prints and returns.

````
Correct!
````

- If the guess is incorrect and the user has no more guesses, it prints (where `hidden` is the value of the passed parameter `hidden`) and returns.

````
I'm sorry, the number was hidden
````

- If the guess is incorrect and the user has guesses remaining, it prints either corresponding to whether or not the guess is higher than `hidden` or lower than `hidden` and then repeats.

```
Higher
````

````
Lower
````

**Example Interactions** (input in **bold**):

````python
guessing_game(42, 3) => None
````

and the following is displayed:

````
50
Lower
25
Higher
38
I'm sorry, the number was 42
````

````python
guessing_game(42, 7) => None
````

and the following is displayed:

````
42
Correct!
````

Please click on the following link for my [solution](https://github.com/itsmichelletrinh/Python/blob/main/Module%203%3A%20Strings%20%26%20Input%20and%20Output/Q2%3A%20Number%20Guessing%20Game.md).

***

## Question #3 and Solution

**3. Write a function**

````python
proper_caps(s)
````
         
**that consumes a string `s` and returns a new string according to the following specifications.**

In the new string, all letters are lowercase unless they are at the start of a sentence. You may assume all sentence-ending punctuation in `s` will be followed by either a single space, or be the last character of `s`. 
We will define a character to be the start of a sentence as either:

- The start of `s` (the first character will always be a letter and should be capitalized).
- The first non-whitespace character immediately after a period, exclamation mark, or question mark (which you may also assume will always be a letter and should be capitalized).

**Example:**

````python
proper_caps("THIS IS A TEST 7. of the caps function") 
   => "This is a test 7. Of the caps function"
````

Please click on the following link for my [solution](https://github.com/itsmichelletrinh/Python/blob/main/Module%203%3A%20Strings%20%26%20Input%20and%20Output/Q3%3A%20Properly%20Capitalize%20a%20String.md).

***
