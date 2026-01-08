````python
import check


def intersect(L, M):
  '''
  Returns a list of distinct integers that are found in both L and M, in the 
  order of appearance in L
  
  intersect: (listof Int) (listof Int) -> (listof Int)
  
  Examples:
    intersect([], [1, 2, 3]) => []
    intersect([1, 2, 3], []) => []
    intersect([1, 2, 3], [4, 1, 5, 2]) => [1, 2]
    intersect([2, 5, 5, 7, 9, 2, 4, 54378], [1, 1, 1, 5, 8, 9, 7]) => [5, 7, 9]
    intersect([2, 5, 5, 7, 9, 2, 4, 104], [1, 1, 1, 5, 8, 9, 7]) => [5, 7, 9]
  '''
  def common(L, M, pos):
    '''
    Returns a list of distinct integers that are found in both L and M, in
    the order of appearance in L by checking each pos of L in M 
    
    common: (listof Int) (listof Int) Nat -> (listof Int)
    '''
    if pos >= len(L):
      return common_lst
    elif L[pos] in M and not(L[pos] in common_lst):
      common_lst.append(L[pos])
    return common(L, M, pos+1)
    
  common_lst = []
  if L == [] or M == []:
    return []
  return common(L, M, 0)

##Examples:
check.expect("MarkUs Basic Test", 
             intersect([2, 5, 5, 7, 9, 2, 4, 104],
                       [1, 1, 1, 5, 8, 9, 7]), [5, 7, 9])
check.expect("L is empty", intersect([], [1, 2, 3]), [])
check.expect("M is empty", intersect([1, 2, 3], []), [])
check.expect("Personal Example", intersect([1, 2, 3], [4, 1, 5, 2]), [1, 2])
check.expect("Provided Example", 
            intersect([2, 5, 5, 7, 9, 2, 4, 54378], [1, 1, 1, 5, 8, 9, 7]),
            [5, 7, 9])
            
##Tests:
check.expect("L and M empty", intersect([], []), [])
check.expect("No Common #s", intersect([1, 2, 3], [4, 5, 6]), [])
check.expect("L and M Same", intersect([1, 2, 3], [1, 2, 3]), [1, 2, 3])
check.expect("L and M Same #s But Different Order",
            intersect([5, 2, 8, 10], [8, 10, 2, 5]), [5, 2, 8, 10])
check.expect("One List Same #s", intersect([1, 1, 1], [3, 1, 4]), [1])
check.expect("Negative #s", intersect([-6, -10, 1], [-5, -6, 2]), [-6])
````
