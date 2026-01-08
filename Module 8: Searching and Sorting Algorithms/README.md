# Module 8 Assignment Questions

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
(e.g. dictionaries, commands continue or break, zip, functions with default parameters, left hand slicing
(experessions of the form L[:] = ... where L is a list), anything with set or enumerator, ord, chr, try and
except, list comprehension, etc.).

Do not mutate passed parameters for required functions unless otherwise told to.

Use only the functions, methods, operations, constants and keywords as follows:

- abs, len, max, min, sum and range (however keyword parameters for these functions are not allowed and sum
  should only consume a single list parameter)
- sort method and sorted with keyword parameters key and reverse
- Any method or constant in the math module
- Any basic arithmetic or comparison operations (+, -, *, /, //, %, **, <, <=, ==, != >, >=)
- Any basic logical operators (not, and, or)
- These typecasting operators: int(), str(), float(), bool(), list(), and type()
- if statements (including elif and else)
- String or list slicing and indexing as well as string or list operations using the operators above
- Any string or list methods listed below and the in operator
- input and print as well as the formatting parameter end and method format. Note that all prompts must match
  exactly in order to obtain marks, so ensure that you do not alter these prompts.
- Recursion is allowed but inputs will often be larger than recursion can handle so be cautious!
- Abstract List Functions map and filter and the keyword lambda
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
reverse', 'sort')
````

***

## Question #1 and Solution

Remember **Intersect** from A4Q1, A4Q2, A6Q1 and A6Q4? Clearly four times isn't enough! Let us do it one last time!

**1. Write a function**

````python
intersect(L, M)
````
         
**that consumes two sorted lists of integers `L` and `M`, and returns a sorted list that contains only elements common to both lists.**

You must obey the following restrictions:

- No recursion or abstract list functions,
- `intersect` must run in O(n) where n is the combined length of the two parameters.

**Sample:**

````python
intersect([2, 2, 4, 5, 5, 7, 9, 7], [1, 1, 1, 5, 7, 8, 9]) => [5, 7, 9]
````

**Hint:**

As the title hints at, you are mostly doing the same thing as the merge function from merge sort. Mostly.

Please click on the following link for my [solution]().

***

## Question #2 and Solution

**2. Write a function**

````python
find_first(corpus, prefix)
````
         
**that consumes `corpus`, a sorted list of unique strings and `prefix` a string of size at most 1000, and returns the first string in `corpus` that starts with `prefix` or `None` if no such string exists. Your code must run in O(log n) time.**

**Example:**

````python
find_first(["beaufort",
            "bleu",
            "brie",
            "camembert",
            "cantal",
            "comte",
            "maroille",
            "munster",
            "reblochon",
            "z7"], "ca") => "camembert"
````

Please click on the following link for my [solution]().

***

## Question #3 and Solution

For this problem, we define the data type `nestof` which can be used in your design recipe elements:

````python
## A (nestof X) is (listof (anyof X (nestof X)))
````

Intuitively, a `nestof` is a nested lists of arbitrary depths.

For example, ["a", "b", ["ew", "d", ["r", "j"], "", ["a"]], []] is a `nestof` strings.

We call **siblings** nest values contained inside the same list, for example "d", ["r", "j"] and ["a"] are some siblings in the example above.

**3. Write a function**

````python
nest_sort(N)
````
         
**that consumes `N`, a (`nestof Int`), returns `None`, and mutates `N` to be in sorted order in according to the following rules:**

- A `nest` should come before a sibling `nest` if the sum of all the integers it contains is smaller than the sum of the integers the other nest contains; for example [9] should come before [2, 5, [3]] (the sum of all inner integers here is 10).
- If the sum of the integers contained in two sibling nests are equal, they keep the order they had.
- An integer should come before a sibling nest if it is smaller than the sum of all the integers the nest contains; for example 9 should come before [4, 3, 3]
- If an integer is equal to the sum of the integers contained in a sibling nest, they keep the order they had.
- If two integers are equal... It does not matter, they are the same anyway.

The function `nest_sort` must run in O(n log n) where n is the sum of the number of individual integers across all `nest`s and the value of `depth(N)` as in the code below.

**Examples:**

````python
nest = [16, 8, 5481792, [2, 4], 0, 6, 4, [19, [4, 3]]]
nest_sort(nest) => None
````

and nest is now 

````python
[0, 4, [2, 4], 6, 8, 16, [[3, 4], 19], 5481792]
````

**Hints:**

- This problem seems scary but really the solution is not far off from our Merge Sort algorithm we've already done.
- Remember that length one nests that are lists should also be sorted.
- Review the `type()` command from Module 1. For example,

````python
type([]) == type([2,[3]]) => True
````

- For positive integers m, n, r, if m * r <= n, then m * rlog(r) < n log(n).
- You may use the flatten function provided which runs in O(n) where n is the sum of the length of the final list and the `depth` of the passed parameter.
- Don't stress about recursion depth limits (we know what your code should be able to handle).

Please click on the following link for my [solution]().

***
