# Module 1 Assignment Questions

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
Natural numbers in this course begin at 0. Positive integers start at 1.
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
from later modules (e.g., if statements, dictionaries, loops (for, while, or others), zip, functions with
default parameters, sorted, anything with sets or enumerators, slicing, indexing (square brackets), string
methods, and/or lists, ord, chr, try and except). Use only the functions, methods, operations, constants
and keywords as follows: abs, len, max, and min (however keyword parameters for these functions are
not allowed)
Any method or constant in the math module
Any basic arithmetic operation (+, -, *, /, //, %, **)
These typecasting operators: int(), str(), float(), and type()
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

**1. How many pizzas does it take to feed a party?**  This is something we can figure out with a little bit of math.

Write a Python function

````python
how_many_pizzas(slices_veg, slices_meat, slices_deluxe)
````
         
that consumes three natural numbers: `slices_veg`, `slices_meat`, and `slices_deluxe`; and returns a natural number corresponding to the minimum number of pizzas to order, under the assumption that each pizza contains exactly 8 slices, all of which must be the same type (no half-and-half pizzas are allowed, etc.).

Example:

````python
how_many_pizzas(3, 16, 7) => 7
````

**Explanation**: We require at least 1 vegetarian, 2 meat, and 7 deluxe pizzas.

**Hint**: You will find the function `math.ceil` useful.

Please click on the following link for my [solution](https://github.com/itsmichelletrinh/Python/blob/main/Module%201%3A%20Introduction%20to%20Programming%20in%20Python/Q1%3A%20Minimum%20Number%20of%20Pizzas.md).

***

## Question #2 and Solution

Converting a useful formula to Python.

When dealing with most vehicles, you may want to work out how far you can go on a tank of gas. However, when dealing with rocketry, it’s much more meaningful to work out how much the rocket is able to change its velocity.

You can work this out from three numbers:

`m0`, the rocket’s initial mass (including fuel)
`mf`, the rocket’s final mass (after burning all fuel)
`isp`, the rocket motor’s "specific impulse" (a measurement of efficiency)
Given these values, you can compute velocity using the following equation:

<img width="209" height="69" alt="image" src="https://github.com/user-attachments/assets/c48fb850-579e-457b-993e-0317c259f0f2" />

where `g0` is standard gravity (9.80665m/s2).

**2. Write a Python function**

````python
delta_v(m0, mf, isp)
````
         
**which consumes three positive integers `m0`, `mf`, and `isp` representing the values above and returns the value for velocity.**

**Example**:

````python
delta_v(7, 7, 320) => 0.0
````

You can use the online calculator linked here to check your results. Make sure to set it to "specific impulse" not "exhaust velocity."

Note that this is a floating point value, so you must use check.within for your testing. Since the online calculator only has 2 digits after the decimal, your check.within tests may use **0.01** as the tolerance (of course, you could also just use the calculator app on your phone / computer to get more digits).

**Hint**: You will find the function `math.log` useful.

Please click on the following link for my [solution](https://github.com/itsmichelletrinh/Python/blob/main/Module%201%3A%20Introduction%20to%20Programming%20in%20Python/Q2%3A%20Calculate%20Velocity.md).

***

## Question #3 and Solution

When dealing with numbers like credit card numbers and student numbers, it’s useful to have a quick way to detect data entry errors. A common solution is the Luhn Algorithm where the digits of a number are added together. If the sum is divisible by 10, the number is considered to be valid, otherwise it is not.

This is commonly done by taking an existing number (e.g. a bank account number) and adding an additional digit, called a "check digit," so that it will pass Luhn’s Algorithm.

**3. Write the Python function**

````python
add_check(n)
````
     
**that consumes a 4 digit natural number `n`, and adds a check digit to it (to the right, i.e. the "ones" column).**

**Note**: You are not required to check whether or not the number is valid, only to add a check digit to n to make it valid.

**Example**:

````python
add_check(8675) => 86754
````

**Explanation**: Notice that 8+6+7+5=26. This is 4 away from 30, so the check digit must be 4.

Please click on the following link for my [solution](https://github.com/itsmichelletrinh/Python/blob/main/Module%201%3A%20Introduction%20to%20Programming%20in%20Python/Q3%3A%20Luhn%20Algorithm.md).

***
