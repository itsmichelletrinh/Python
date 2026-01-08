````python
import check


def octal_to_int(s):
  '''
  Returns the octal decimal value of s as a natural number 
  
  octal_to_int: Str -> Nat
  Requires:
    s != ""
    int(s) >= 0
  
  Examples: 
    octal_to_int("0") => 0
    octal_to_int("11") => 9
    octal_to_int("721") => 465
    octal_to_int("1742454") => 509228
  '''
  s_length = len(s)
  
  def str_position(s, s_length, pos):
    '''
    Returns the octal decimal value of s as a natural number by adjusting
    the original length of s, s_length, as the exponents, for each individual 
    digit in s indicated by pos 
    
    str_position: Str Nat Nat -> Nat
    '''
    if pos >= len(s):
      return 0
    return int(s[pos]) * 8**(s_length - 1) + \
    str_position(s, s_length - 1, pos + 1)
    
  return str_position(s, s_length, 0)

##Examples:
check.expect("MarkUs Basic Test", octal_to_int("721"), 465)
check.expect("Provided Example", octal_to_int("1742454"), 509228)
check.expect("Base Case", octal_to_int("0"), 0)
check.expect("Personal Generic Example", octal_to_int("11"), 9)

##Tests:
check.expect("0 Value", octal_to_int("102"), 66)
check.expect("Larger String", octal_to_int("123456789"), 21913097)
````
