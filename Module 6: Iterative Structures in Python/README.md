# Module 5 Assignment Questions

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
Do not import any modules other than math and check. You are always allowed to define your own
helper/wrapper functions, as long as they meet the assignment restrictions. Do not use Python constructs
from later modules (e.g. dictionaries, commands continue or break, zip, functions with default parameters,
left hand slicing (experessions of the form L[:] = ... where L is a list), sorted, anything with set or
enumerator, ord, chr, try and except, list comprehension, etc.).

For this assignment specifically, abstract list functions, map, and filter are not allowed.
Recursion is also prohibited!

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
  match exactly in order to obtain marks, so ensure that you do not alter these prompts.
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

In this section, you will repeat a previous assignment problem **except you will not be allowed to use recursion nor abstract list functions**! You do not need any non-body design recipe elements for this problem 
(though you might want to copy your tests from the previous problem to help here).

The problem is repeated below for convenience.

**1. Write the function**

````python
intersect(L, M)
````
         
**that consumes two lists of integers `L` and `M` and returns a list that contains the elements in common between the two lists in the order of first appearance in the first list.**

**Example:**

````python
intersect([2, 5, 5, 7, 9, 2, 4, 54378], [1, 1, 1, 5, 8, 9, 7]) => [5, 7, 9]
````

Please click on the following link for my [solution]().

***

## Question #2 and Solution

**2. Write a function**

````python
split_list(source, partition_size)
````
         
**that consumes a list of integers `source` and a positive integer `partition_size`, and returns a list of lists of integers containing all elements of `source` split amongst lists of `partition_size` elements (except the last one that might be smaller).**

**Examples:**

````python
split_list([1, 2, 3, 4, 5, 6, 7, 8, 9], 4) => [[1, 2, 3, 4], [5, 6, 7, 8], [9]]
split_list([], 49924312) => []
````

Please click on the following link for my [solution]().

***

## Question #3 and Solution

Rock Paper Scissors (also known as Ro-Sham-Bo) is a hand game usually played between two people, in which each player simultaneously forms one of three shapes with an outstretched hand. These shapes are "rock", "paper", and "scissors". 
A simultaneous, zero-sum game, it has only three possible outcomes: a draw, or a win for one player and a loss for the other (or vice versa). A player who decides to play rock will beat another player who has chosen scissors ("rock crushes scissors"), 
but will lose to one who has played paper ("paper covers rock"); a play of paper will lose to a play of scissors ("scissors cuts paper"). If both players choose the same shape, the game is tied and is immediately replayed to break the tie. 
The following diagram illustrates the game:

<img width="566" height="456" alt="image" src="https://github.com/user-attachments/assets/c7e64ef9-db71-48c3-a72f-cfb14b12b8e7" />

**3. Write a function**

````python
ro_sham_bo(total_winning_throws)
````
         
**that consumes a positive integer and returns None. The function runs a suite of Ro Sham Bo games that ends when a player reaches a total total_winning_throws won games. Players record their choice one after the other by typing scissors, paper or rock 
when prompted by the function. After each throw except the final winning throw, the function prints out the status of the game. If a user enters an invalid entry, an error message is displayed and the player is prompted again to enter a valid entry.** 
See the example below for more information on the prompts.

**Example:**

````python
ro_sham_bo(2)=>None
````

and the follow is output with input in bold:

````python
Player 1's hand: paper
Player 2's hand: scissors
Player 1: 0, Player 2: 1
Player 1's hand: 70
Error. Not a valid option.
Player 1's hand: scissors
Player 2's hand: scissors
Tie!
Player 1: 0, Player 2: 1
Player 1's hand: rock
Player 2's hand: scissors
Player 1: 1, Player 2: 1
Player 1's hand: rock
Player 2's hand: paper
Player 2 wins!
````

Please click on the following link for my [solution]().

***

## Question #4 and Solution

Let's do one more round of `intersect` with a twist.

**4. Write a function**

````python
intersect(source, others)
````
         
**that consumes `source`, a list of integers, and `others` a list of lists of integers. The function mutates `source` by keeping only the numbers that are also in every lists in `others`.**

**Examples:**

````python
source = [1, 4, 6, 2, 1, 677196]
intersect(source, [[4, 1], [6, 9, 1, 4], [0, 2, 2, 2, 4, 2, 1]]) => None
````

and `source` is now 

````python
[1, 4, 1]
````

Please click on the following link for my [solution]().

***
