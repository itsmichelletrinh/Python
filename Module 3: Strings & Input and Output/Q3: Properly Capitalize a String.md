````python
import check


def proper_caps(s):
  '''
  Returns a new string of s such that the start of s is capitalized and the 
  first non-whitespace character after any punctuation is capitalized
  
  proper_caps: Str -> Str 
  
  Examples:
    proper_caps("THIS IS A TEST. of the caps function") => "This is a test. Of 
    the caps function"
    proper_caps("") => ""
    proper_caps("TEST. TEST") => "Test. Test"
  '''
  def str_position(s, pos):
    '''
    Returns a new string of s such that the start of s is capitalized and the 
    first non-whitespace character after any punctuation is capitalized by 
    checking the current character position, pos, with the previous character 
    position for a punctuation (".", "!", "?")
    
    str_position: Str Nat -> Str
    '''
    if pos >= len(s):
      return ""
    elif pos == 0:
      return s[0].capitalize() + str_position(s, pos + 1)
    elif (s[pos-1] != ".") and (s[pos-1] != "!") and (s[pos-1] != "?"):
      return s[pos] + str_position(s, pos + 1)
    elif (s[pos-1] == ".") or (s[pos-1] == "!") or (s[pos-1] == "?"):
      if s[pos].isspace():
        return s[pos] + s[pos+1].capitalize() + str_position(s, pos+2)
      return s[pos].capitalize() + str_position(s, pos + 1)
      
  if s == "":
    return ""
  return str_position(s.lower(), 0)

##Examples:
check.expect("MarkUs Basic Test",
             proper_caps("THIS IS A TEST. of the caps function"),
             "This is a test. Of the caps function")
check.expect("Base Case", proper_caps(""), "")
check.expect("Basic Example", proper_caps("TEST. TEST"), "Test. Test")
             
##Tests:
check.expect("Punctuation At End", proper_caps("test."), "Test.")
check.expect("! Punctuation", proper_caps("hey! there"), "Hey! There")
check.expect("? Punctuation", proper_caps("heLLO? hI"), "Hello? Hi")
check.expect("Multiple Punctuation", proper_caps("hi! hey? hello."), 
             "Hi! Hey? Hello.")
````
