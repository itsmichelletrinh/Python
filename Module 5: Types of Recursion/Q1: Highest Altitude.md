````python
import check


def alt_max(L):
  '''
  Returns the highest altitude measured from a list of changes (L)
  
  alt_max: (listof Int) -> Nat
  
  Examples: 
    alt_max([0]) => 0
    alt_max([]) => 0
    alt_max([5, -3, 2, 3, -4, -3, -4992447]) => 7
    alt_max([1, 2, 3, -5]) => 6
  '''
  def alt_max_acc(L, num, max_num):
    '''
    Returns the highest altitude, stored in max_num, measured from a list of 
    changes, L, while keeping track of the current altitude in num 
    
    alt_max_acc: (listof Int) Int Nat -> Nat
    '''
    if L == []:
      return max_num
    elif num + L[0] >= max_num:
      return alt_max_acc(L[1:], num + L[0], num + L[0])
    elif num + L[0] < max_num:
      return alt_max_acc(L[1:], num + L[0], max_num)
  
  return alt_max_acc(L, 0, 0)
  
##Examples:
check.expect("MarkUs Basic Test", alt_max([5, -3, 2, 3, -4, -3]), 7)
check.expect("Base Case, Empty List", alt_max([]), 0)
check.expect("Base Case, No Changes", alt_max([0]), 0)
check.expect("Personal Example", alt_max([1, 2, 3, -5]), 6)

##Tests:
check.expect("Only Negative Changes", alt_max([-5, -2, -1]), 0) 
check.expect("Large Increase", alt_max([3287, 280, -100]), 3567)
check.expect("No Change Inbetween", alt_max([10, 55, 0, -50]), 65)
check.expect("Full List No Changes", alt_max([0, 0, 0]), 0)
````
