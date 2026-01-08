# Module 10 Assignment Questions

## 📚 Table of Contents
- [Instructions](#instructions)
- [Question #1 and Solution](#question-1-and-solution)

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
functions, as long as they meet the assignment restrictions. Do not use Python constructs not taught in this
course (e.g. commands continue or break, zip, functions with default parameters, left hand slicing (experessions
of the form L[:] = ... where L is a list), anything with set or enumerator, with, try and except etc.).

Do not mutate passed parameters for required functions unless otherwise told to.

Use only the functions, methods, operations, constants and keywords as follows:

- abs, len, max, min, sum, range, isinstance, ord and chr (however keyword parameters for these functions are
  not allowed and sum should only consume a single list parameter)
- sort method and sorted with keyword parameters key and reverse
- Any method or constant in the math module
- Any basic arithmetic or comparison operations (+, -, *, /, //, %, **, <, <=, ==, != >, >=)
- Any basic logical operators (not, and, or)
- These typecasting operators: int(), str(), float(), bool(), list(), and type()
- if statements (including elif and else)
- String or list slicing and indexing as well as string or list operations using the operators above
- Any string, list or dictionary methods (see additional notes below) and the in operator
- Classes and magic methods
- input and print as well as the formatting parameter end and method format (note that all prompts must match
  exactly in order to obtain marks, so ensure that you do not alter these prompts)
- Loops, specifically while loops and single variable for loops.
- Recursion is allowed but inputs will often be larger than recursion can handle so be cautious!
- Abstract list functions map and filter and the keyword lambda
- Basic file input or output operations (open, close, readline, readlines, write, writelines)

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

This assignment consists of a large single "project" question with multiple parts. Completing earlier parts will be important to completing later parts. Be sure to come to office hours and ask for help if needed.

In this assignment we will be detecting plagiarism in English essays. This will be done in several stages.

## Part A

Before we can even begin comparing text, we must pre-process it so that we will not be fooled by extra commas, OdD cAsEs, etc.

**Write the function**

````python
preprocess_text(s)
````

**that consumes a string `s` and returns the pre-processed string. Use the following pre-processing rules:**

1. All letters are replaced with their lower case equivalent.
2. Numbers, dashes ('-'), and slashes ('/') are left as is.
3. Apostrophes are only kept if they are in between two letters (that is, we want to ignore 'single quotes' but do not want to ignore the difference between it's and its).
4. All consecutive whitespace characters (meaning ' ' and '\n' characters) are replaced with a single space character.
5. The returned string should not begin or end with a whitespace.
6. All other characters not mentioned above are removed (e.g., '+' and '!'). Note that this might cause you to need to remove spaces again!

**Example:**

````python
preprocess_text("This is a 'test'!\n Try with  2-4-grams.")
      => "this is a test try with 2-4-grams"
````

The capitals are replaced with lower case; the exclamation mark, period, and single quotes are removed; the two spaces before 2-4 are replaced with one space; and the newline and space before 
"Try" are also replaced with one space.

**For full correctness marks your function should be O(n) where n is the length of the string.**

## Part B

Once the document has been processed, we must break it into something called "n-grams." An n-gram is a length n substring.

Consider the string "`exuberant`". It contains the following 2-grams: `['ex', 'xu', 'ub', 'be', 'er', 'ra', 'an', 'nt']`. If you instead were interested in 5-grams: `['exube', 'xuber', 'ubera', 'beran', 'erant']`.

For most uses of n-grams, the order does not matter. We will represent the n-grams for a document as a dictionary where the keys are n-grams, and the values are the number of duplicates.

**Write the function**

````python
get_ngrams(text, n, fnameout)
````

**that consumes a string `text`, a positive integer `n`, and a string `fnameout`. The function returns the n-gram dictionary, where the `n` parameter is the length of the n-grams to extract. 
The code should also write each n-gram in ASCII (lexicographical) order with its associated count, comma separated, to the file with name `fnameout`. Each line, including the last, should end with a newline character 
(excepting the empty file which should just be empty). If the length of `text` is less than `n`, then there are no n-grams for this text and the output file should be empty.**

For simplicity, you can assume the `text` will be pre-processed (that is, it will be the output of something from the previous part).

For testing, make sure you include a comment that describes what should be in the expected output files for your tests for marking purposes.

**Examples:**

````python
get_ngrams("banana", 2, "fruit.txt") => {"ba":1, "an":2, "na":2}
````
  
and `fruit.txt` contains

````python
  an,2
  ba,1
  na,2
````

````python
get_ngrams("499296$ !", 20, "out.txt") => {}
````

and `out.txt` is an empty text file.

## Part C

The Jaccard similarity of two sets A and B is

````python
jaccard(A, B) = size(A intersect B) / size(A union B)
````

If `A = [1, 2, 3]` and `B = [2, 3, 4]` then `A union B = [1, 2, 3, 4]` and `A intersect B = [2, 3]`. The Jaccard score will be `2 / 4 = 0.5`, meaning a 50% match.

On the other hand, `A union A = [1, 2, 3]` and `A intersect A = [1, 2, 3]`, so the Jaccard score will be `3 / 3 = 1.0`, meaning a 100% match.

We will extend this concept to n-gram dictionaries. To do that, we must define the size of a dictionary, as well as union and intersection.

- The size of an n-gram dictionary is the sum of the values of all elements. For example, the size of `{"ba": 1, "an": 2, "na": 2}` is `5`.
- The union of n-gram dictionaries `A` and `B` will contain all n-grams that are in either `A` or `B` (just like a set union) and the count will be the *maximum* count for that key. For example,

````python
union({'a': 1, 'b': 2, 'c': 2}, {'a': 2, 'c': 1}) => {'a': 2, 'b': 2, 'c': 2}
````

- The intersection of n-gram dictionaries `A` and `B` will contain all keys that are in both `A` and `B` (just like a set intersection) and the count will be the *minimum* count for that key. For example,

 ````python 
intersection({'a': 1, 'b': 2, 'c': 2}, {'a': 2, 'c': 1}) => {'a': 1, 'c': 1}
````

**Using the above definition, write the function**

````python
jaccard_ngram(ngram1, ngram2)
````

**that consumes two n-gram dictionaries in `ngram1` and `ngram2` (that is, dictionaries where each key is a string of the same size and the value associated is a positive integer) and returns the Jaccard similarity score.**

As a special case, when both dictionaries are empty, the similarity should be `1.0` (100% match). This avoids a nasty division by 0 error that would otherwise occur.

**Example:**

````python
jaccard_ngram({'ba': 1,'na': 2, 'an': 2}, {'ba': 1, 'na': 1, 'an': 1}) => 0.6
````

The intersection has a size of 3 and the union has a size of 5. So, the Jaccard similarity score will be `3 / 5 = 0.6`, or 60%.


## Part D

Finally, **write the function**

````python
document_similarity(filename1, filename2, n)
````

**which consumes two strings (file names), and `n`, a positive integer value. The function returns a floating point value equal to the Jaccard multi-set score for the n-grams extracted from the two named files.**

For testing, make sure you include a comment that describes what should be in the input files for your tests for marking purposes. You should also write the results of calling `get_ngrams` to files 
"`_dummy1.txt`" and "`_dummy2.txt`" (though we won't check these files).

Please click on the following link for my [solution](https://github.com/itsmichelletrinh/Python/blob/main/Module%2010%3A%20File%20Input%20and%20Output/Q1%3A%20Detecting%20Plagiarism.md).

***
