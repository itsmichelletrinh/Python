# Module 4 Assignment Questions

## 📚 Table of Contents
- [Instructions](#instructions)
- [Question #1 and Solution](#question-1-and-solution)
- [Question #2 and Solution](#question-2-and-solution)
- [Question #3 and Solution](#question-3-and-solution)
- [Question #4 and Solution](#question-4-and-solution)

Please note that all questions are created by University of Waterloo, School of Computer Science for the CS116: Introduction to Computer Science 2 course.

***

## Instructions
The following instructions were given to students:

- Style Guide

````
Natural numbers in this course begin at 0.
Required functions need all design recipe elements. Functions you define (e.g., helper functions) need all
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
- The in operator and any string or list methods listed below except for using specified keyword parameters
  key and reverse in the sort method (which will be introduced in module 8)
- input and print as well as the formatting parameter end and method format. Note that all prompts must
  match exactly in order to obtain marks so ensure that you do not alter these prompts.
- Recursion
- Abstract List Functions map and filter and the keyword lambda

Read each question carefully for additional restrictions.
````

- Additional Notes

````
While you may use global constants in your solutions, do not use global variables for anything other
than testing.
Read each question carefully for additional restrictions.
The solutions you submit must be entirely your own work. Do not look up either full or partial solutions
on the Internet or in printed sources.

String methods include: ('capitalize', 'casefold', 'center', 'count', 'endswith', 'expandtabs', 'find',
'format', 'index', 'isalnum', 'isalpha', 'isdecimal', 'isdigit', 'isidentifier', 'islower', 'isnumeric',
'isprintable', 'isspace', 'istitle', 'isupper', 'join', 'ljust', 'lower', 'lstrip', 'partition', 'replace',
'rfind', 'rindex', 'rjust', 'rpartition', 'rsplit', 'rstrip', 'split', 'splitlines', 'startswith', 'strip',
'swapcase', 'title', 'upper', 'zfill')

List methods include: ('append', 'clear', 'copy', 'count', 'extend', 'index', 'insert', 'pop', 'remove',
'reverse', 'sort')
````

***

## Question #1 and Solution

**Do not use abstract list functions to solve this question.**

**1. Write the function**

````python
intersect(L, M)
````
         
**that consumes two lists of integers `L` and `M` and returns a list of distinct integers, containing the elements in common between both `L` and `M`, in the order of appearance in `L`.**

**Example:**

````python
intersect([2, 5, 5, 7, 9, 2, 4, 54378], [1, 1, 1, 5, 8, 9, 7]) => [5, 7, 9]
````

Please click on the following link for my [solution](https://github.com/itsmichelletrinh/Python/blob/main/Module%204%3A%20Lists/Q1%3A%20Common%20Integers%20Between%202%20Lists%20with%20Recursion.md).

***

## Question #2 and Solution

In this section, you will repeat the previous assignment problem **except you will not be allowed to use recursion**! You do not need any non-body design recipe elements for this problem (though you might want to copy your tests from the previous problem to help here).

The problem is repeated below for convenience.

**2. Write the function**

````python
intersect(L, M)
````
         
**that consumes two lists of integers `L` and `M` and returns a list of distinct integers, containing the elements in common between both `L` and `M`, in the order of appearance in `L`.**

**Example:**

````python
intersect([2, 5, 5, 7, 9, 2, 4, 54378], [1, 1, 1, 5, 8, 9, 7]) => [5, 7, 9]
````

Please click on the following link for my [solution](https://github.com/itsmichelletrinh/Python/blob/main/Module%204%3A%20Lists/Q2%3A%20Common%20Integers%20Between%202%20Lists%20with%20Abstract%20List%20Functions.md).

***

## Question #3 and Solution

**3. Write the function**

````python
restrict(source, maximums)
````
         
**that consumes two lists of integers of the same length, `source`, and `maximums`. The function `restrict` mutates `source` so that for every number it contains is smaller than or equal to the number at the same index in `maximums`.** 

This is done by leaving the entry alone if it is less than the corresponding entry in `maximums` or by setting the value in source to the corresponding value in `maximums`.

**Example:**

````python
L = [3, 6, 0, -2, 4]
restrict(L, [0, 10, 7, 0, -10]) => None
````

and `L` is mutated to 

````python
[0, 6, 0, -2, -10]
````

Please click on the following link for my [solution](https://github.com/itsmichelletrinh/Python/blob/main/Module%204%3A%20Lists/Q3%3A%20Mutate%20a%20List%20to%20Contain%20Smaller%20or%20Equal%20Numbers%20as%20Another%20List.md).

***

## Question #4 and Solution

Minesweeper is a single-player puzzle video game. The objective of the game is to clear a rectangular board containing hidden “mines” or bombs without detonating any of them, with help from clues about the number of neighboring mines in each field. 
The game originates from the 1960s, and has been written for many computing platforms in use today. You can find out more about Minesweeper [here](https://en.wikipedia.org/wiki/Minesweeper_(video_game)).

You can also play Minesweeper for free at [this address](https://freeminesweeper.org/). But be careful! You have an assignment to do.

**4. Implement the function**

````python
create_minesweeper_grid(width, height, mine_coordinates)
````
         
**that consumes `width` and `height`, two positive integers, and `mine_coordinates`, a list of lists of two natural numbers containing the coordinates of the mines. The function `create_minesweeper_grid` returns a list of list of strings representing the 
minesweeper grid, according to these criteria:**

- Each cell representing a mine contains the string “X”.
- Each cell that is not in the vicinity of any mine contains the empty string.
- Every other cell contains a string representing the number of mines in the adjacent cells (including diagonals).

The mine coordinates in `mine_coordinates` must be distinct and within `grid`.

**Example:**

````python
create_minesweeper_grid(5, 3, [[1,1], [2,2], [1,2]]) 
   => [["1", "2", "2", "1", ""],
       ["1", "X", "X", "2", ""],
       ["1", "3", "X", "2", ""]]
````
                                          
**Tips:**

**Be very careful about making the grid.** We're given you a helper function you should use to help initially make the 2D list to avoid repeated references.

Consider grouping repetitive operations in a helper function to improve the readability of your code.

Please click on the following link for my [solution](https://github.com/itsmichelletrinh/Python/blob/main/Module%204%3A%20Lists/Q4%3A%20Minesweeper.md).

***
