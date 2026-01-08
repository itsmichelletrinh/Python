````python
import check


def count_chars(s, chars):
  '''
  Returns a list representing how many of each character in chars is found in s
  
  count_chars: Str Str -> (listof Nat)
  
  Examples:
    count_chars("", "a") => [0]
    count_chars("Hi", "") => []
    count_chars("", "") => []
    count_chars("Hello, world! This is a test", "aeiou") => [1, 2, 2, 2, 0]
    count_chars("Hello there Number 1636176", "h") => [1]
    count_chars("My name is Michelle", "abc") => [1, 0, 1]
  '''
  def count_chars_acc(s, loc, acc):
    '''
    Returns a list, stored in acc, that represents how many of each character 
    in loc is found in s
    
    count_chars_acc: Str (listof Str) (listof Nat) -> (listof Nat)
    '''
    if loc == []:
      return acc
    elif loc[0] in s:
      return count_chars_acc(s, loc[1:], acc + [s.count(loc[0])])
    return count_chars_acc(s, loc[1:], acc + [0])

  return count_chars_acc(s, list(chars), [])

##Examples:
check.expect("MarkUs Basic Test", 
             count_chars("Hello, world! This is a test", "aeiou"),
             [1, 2, 2, 2, 0])
check.expect("Provided Example",
             count_chars("Hello there Number 1636176", "h"), [1])
check.expect("Base Case, Empty s", count_chars("", "a"), [0])
check.expect("Base Case, Empty chars", count_chars("Hi", ""), [])
check.expect("Empty Strings", count_chars("", ""), [])
check.expect("Personal Example",
             count_chars("My name is Michelle", "abc"), [1, 0, 1])

##Tests:
check.expect("Mix",
             count_chars("Let's check for a mix of stuff! Including letters, \
             numbers (ex. 123), punctuation, etc.", "abcLIN123!?."), 
             [2, 1, 5, 1, 1, 0, 1, 1, 1, 1, 0, 2])
check.expect("Duplicate in Chars", 
            count_chars("My name is Michelle", "aaa"), [1, 1, 1])
check.expect("Spaces", count_chars("My name is Michelle", " "), [3])
````
