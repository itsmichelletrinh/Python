# Module 9 Assignment Questions

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
(e.g. commands continue or break, zip, functions with default parameters, left hand slicing (experessions of
the form L[:] = ... where L is a list), anything with set or enumerator, ord, chr, try and except, list
comprehension, etc.).

Do not mutate passed parameters for required functions unless otherwise told to.

Use only the functions, methods, operations, constants and keywords as follows:

- abs, len, max, min, sum, range and isinstance (however keyword parameters for these functions are not
  allowed and sum should only consume a single list parameter)
- sort method and sorted with keyword parameters key and reverse
- Any method or constant in the math module
- Any basic arithmetic or comparison operations (+, -, *, /, //, %, **, <, <=, ==, != >, >=)
- Any basic logical operators (not, and, or)
- These typecasting operators: int(), str(), float(), bool(), list(), and type()
- if statements (including elif and else)
- String or list slicing and indexing as well as string or list operations using the operators above
- Any string, list or dictionary methods listed below and the in operator
- Recursion is allowed but inputs will often be larger than recursion can handle so be cautious!
- Abstract List Functions map and filter and the keyword lambda
- Classes and magic methods
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

Dictionary methods include: ('clear', 'copy', 'fromkeys', 'get', 'items', 'keys', 'pop', 'popitem', 'setdefault',
'update', 'values’)
````

***

## Question #1 and Solution

Remember Q2 from A2? Let's go a bit further.

**1. Write the function**

````python
largest_edge_group(vertices)
````
         
**that consumes `vertices`, a list of two-element lists of integers containing the coordinates of the consecutive vertices of a simple polygon (see here for a definition if needed). The function `largest_edge_group` returns the size of the largest group 
of same length edges.**

Your function must run in O(n), where n is the length of vertices.

**Example:**

````python
largest_edge_group([[0,0],[1,1],[0,2],[-2,3],[-1,2],[-7,-7]]) => 3
````

**Hint:**

Remember, it is not possible to compare `floats` for strict equality, but since the coordinates are integers, the squared distance is too.

Please click on the following link for my [solution]().

***

## Question #2 and Solution

Below is the start of the `Date` class:

````python
class Date:
   '''
   Fields: 
      day (Nat)
      month (Nat)
      year (Nat)
      
   Requires: 
      year >= 1800
      day month year corresponds to a valid date in the Gregorian Calendar
   '''
   def __init__(self, d, m, y):
     ##YOUR CODE GOES HERE
     pass
	 
   def __repr__(self):
     ##YOUR CODE GOES HERE
     pass
	 
   def __eq__(self, other):
     ##YOUR CODE GOES HERE
     pass

   def add_days(self, n):
     ##YOUR CODE GOES HERE
     pass
````

**2. Complete the following:**

- `__init__`: Initializes a `Date` object with `day d`, `month m`, and `year y`.
- `__repr__`: A date when printed should display `Date(day,month,year)` where `day`, `month` and `year` are the respective fields of the `Date` object.
- `__eq__`: Dates should be equal if and only if they represent exactly the same date (year, month, and day).
- `add_days`: This method consumes a positive integer number of days, and returns the `Date` that is exactly that many days after `self`.

**Reminder:**

30 days hath September, April, June, and November. All the rest have 31... except February which has 28, or 29 if we are in a leap year. We've provided a function for checking if a year is a leap year.

**Examples:**

````python
  str(Date(1,1,7)) => "Date(1,1,7)"
  Date(1,1,2000) == Date(1,1,2000) => True
  Date(1,1,2000) == Date(1,2,2000) => False
  Date(6,7,2020).add_days(30) => Date(5,8,2020)
````

**Note:**

The `add_days` test in your code depends on the `__eq__` magic method working. We'll use our own working equality when we test your `Date` objects for `add_days`.

Please click on the following link for my [solution]().

***

## Question #3 and Solution

This question will use the following class definition:

````python
class Course:
   ''' 
   Represents a course attempt by a particular student

   Fields: 
      code (Str)
      term (Nat)
      grade (anyof Nat Str)
			          
   Requires: 
      term is 4 digits (e.g. ths term is 1205)
      if grade is a nat, 0 <= grade <= 100
      if grade is a str, it is one of "WD", "WF", "DNW", "INC", "CR", "NCR"
   '''
	  
  def __init__(self, code, term, grade):
    self.code = code 
    self.term = term
    self.grade = grade
	  
  def __repr__(self):
    return "Course({0}, {1}, {2})".format(self.code, self.term, self.grade)
  
  def __eq__(self,other):
    return isinstance(other,Course) and \
           self.code == other.code and \
           self.term == other.term and \
           self.grade == other.grade
````

**3. Write the following functions that deal with a (`listof Course`):**

1. `course_list_by_term` that consumes a list of `Course`s and returns a dictionary where the keys are terms covered by the courses in the consumed list, and the values are lists of courses the student took that term.
   The list of courses should be in the same relative order they were in the consumed list.
         
2. `term_average` that consumes a list of `Course`s and returns a dictionary where the keys are terms covered by the courses in the consumed list, and the values are the student's average grades that term, or `None` if no courses in a term count toward the average.
   Note that grades less than 32 count as 32 towards your average (but for the next part, use the actual average value to compute the highest grade). Further, for non-numerical grades:
   - WD, INC, CR, NCR do not count toward your average
   - WF and DNW count as a 32
         
3. `highest_grade` that consumes a list of courses, and returns a dictionary where the keys are course codes, and the values are the highest numerical grades achieved in each course. If a course has no numerical grades recorded, it is excluded from the dictionary.
         
**Examples:**

````python
CS115 = Course("CS115", 1199, 75)
MATH135 = Course("MATH135", 1199, 80)
CS116a = Course("CS116", 1201, "NCR")
MATH136 = Course("MATH136", 1201, "CR")
CS116b = Course("CS116",1205, 80)
CSgrad = Course("CS7",1205, 80)
example_list = [CS115, MATH135, CS116a, MATH136, CS116b]	  
	  
course_list_by_term(example_list) =>
  {1199:[CS115, MATH135],
   1201:[CS116a, MATH136],
   1205:[CS116b]}
             
term_average(example_list) =>
  {1199:77.5, 1201:None, 1205:80.0}
	     
highest_grade(example_list) =>
  {"CS115":75,
   "MATH135":80,
   "CS116":80}
````

**Reminder:**

The order of keys in a dictionary isn't important!

Please click on the following link for my [solution]().

***
