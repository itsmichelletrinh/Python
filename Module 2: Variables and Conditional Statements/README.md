# Module 2 Assignment Questions

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
from later modules (e.g. dictionaries, loops (for or while or others), zip, functions with default
parameters, sorted, anything with sets or enumerators, slicing, indexing (square brackets), string
methods, and/or lists, ord, chr, try and except).

Use only the functions, methods, operations, constants and keywords as follows:

abs, len, max, and min (however keyword parameters for these functions are not allowed)
Any method or constant in the math module
Any basic arithmetic or comparison operations (+, -, *, /, //, %, **, <, <=, ==, != >, >=)
Any basic logical operators (not, and, or)
These typecasting operators: int(), str(), float(), bool(), and type()
if statements (including elif and else)
Recursion
````

- Additional Notes

````
While you may use global constants in your solutions, do not use global variables for anything other
than testing.
Read each question carefully for additional restrictions.
The solutions you submit must be entirely your own work. Do not look up either full or partial solutions
on the Internet or in printed sources.
````

***

## Question #1 and Solution

**1. Write a function**

````python
harmonic(n)
````
         
**that consumes a positive integer `n` and returns the nth harmonic number:**

<img width="344" height="75" alt="image" src="https://github.com/user-attachments/assets/fd951614-5936-40ac-87f6-dbc9d289de36" />

The last symbol is a summation symbol which is a short hand for the sum in the middle above. We will see this later in the course.

**Note:**

As you have seen, there is a limit to the level of recursive calls that can be made in Python. For that reason, we will only test your code with small values of `n`. You should not add this as restriction of the contract, however.

**Examples:**

````python
harmonic(3) => 1.8333333... #(1 + 1/2 + 1/3)
````

Please click on the following link for my [solution](https://github.com/itsmichelletrinh/Python/blob/main/Module%202%3A%20Variables%20and%20Conditional%20Statements/Q1%3A%20Harmonic%20Numbers.md).

***

## Question #2 and Solution

**2. Write a function**

````python
total_equal_sides(ax, ay, bx, by, cx, cy, dx, dy):
````
         
**that consumes eight integers: `ax` and `ay` (the first vertex), `bx` and `by` (the second vertex), `cx` and `cy` (the third vertex), and `dx` and `dy` (the fourth vertex); all corresponding to points on the Cartesian plane. 
The function `total_equal_sides` returns the number of sides of the quadrilateral formed by the previous vertices that have the same length.** 

Please note that the coordinates will be listed so the first four coordinates correspond to a side of the quadrilateral, the four middle coordinates to a second side, the four end coordinates a third side, and the two coordinates 
at the beginning and end make up a fourth side, all of a non-degenerate quadrilateral (i.e., the input we will test your function on will correspond to genuine quadrilaterals).

**Example 1**

<img width="213" height="111" alt="image" src="https://github.com/user-attachments/assets/372de289-df2f-4f87-8982-49e92f572f3f" />

````python
total_equal_sides(30, 30, 10, -10, -30, 20, -20, 30) => 2
````

**Example 2**

<img width="159" height="89" alt="image" src="https://github.com/user-attachments/assets/611a9dfd-547f-41a5-9cab-2768fd14e972" />

````python
total_equal_sides(60, 10, 10, 10, 40, -15, 60, -15) => 0
````

**Example 3**

<img width="173" height="92" alt="image" src="https://github.com/user-attachments/assets/c8448b6c-0ee2-49aa-aca7-bd47259d93d9" />

````python
total_equal_sides(60, 10, 10, 10, 10, -15, 60, -15) => 2
````

**Tips:**

Calculating the length of the side of a polygon from its vertices requires the use of a square root. Square roots produce real numbers. As you have seen, computers approximate real numbers as floating-point values, and cannot reliably compare them for strict equality. 
However, since y=x implies that sqrt(y) = sqrt(x), you may compare squared side lengths instead of side lengths and work with integers only: 

<img width="262" height="34" alt="image" src="https://github.com/user-attachments/assets/9be0143b-bac8-4615-a834-a51b0e13f48d" />

Please click on the following link for my [solution](https://github.com/itsmichelletrinh/Python/blob/main/Module%202%3A%20Variables%20and%20Conditional%20Statements/Q2%3A%20Total%20Quadrilateral%20Sides%20With%20Same%20Length.md).

***

## Question #3 and Solution

**3. Write a function**

````python
total_prime_factors(n)
````
         
**that consumes a positive integer `n` and returns the number of prime factors it has.**

**Examples:**

````python
total_prime_factors(3)   => 1    # 3
total_prime_factors(10)  => 2    # 2 and 5
````

**Note:**

As you have seen, there is a limit to the level of recursive calls that can be made in Python. For that reason, we will only test your code with small values of `n`. You should not add this as restriction of the contract, however.

Please click on the following link for my [solution](https://github.com/itsmichelletrinh/Python/blob/main/Module%202%3A%20Variables%20and%20Conditional%20Statements/Q3%3A%20Total%20Prime%20Factors.md).

***
