````python
import check


def base_convert(n, s):
  '''
  Returns n converted to string in a base denoted by the length of s
  
  base_convert: Nat Str -> Str 
  Requires:
    len(Str) >= 2
  
  Examples:
    base_convert(0, "01") => "0"
    base_convert(17, "01234567") => "21"
    base_convert(17, "abcdefghij") => "bh"
    base_convert(10, "0123abc") => "13"
  '''
  def base_convert_acc(n, s, acc):
    '''
    Returns n converted to a string, stored in acc, in a base denoted by the 
    length of s  
    
    base_convert_acc: Nat Str Str -> Str
    '''
    if n == 0 and acc == "":
      return str(s[0])
    elif n == 0:
      return acc
    return base_convert_acc(n // len(s), s, s[n % len(s)] + acc)
      
  return base_convert_acc(n, s, "")

##Examples:
check.expect('MarkUs Basic Test', base_convert(17, 'abcdefghij'), 'bh')
check.expect("Provided Example", base_convert(17, "01234567"), "21")
check.expect("Base Case", base_convert(0, "01"), "0")
check.expect("Personal Example", base_convert(10, "0123abc"), "13")

##Tests:
check.expect("Larger #", base_convert(921, "0123abc"), "2aba")
check.expect("Mix s", base_convert(123, "!?1a2"), "22a")
````
