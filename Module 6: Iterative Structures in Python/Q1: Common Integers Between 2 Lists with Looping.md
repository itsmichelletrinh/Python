````python
import check


def intersect(L, M):
  common_lst = []
  
  for num in L:
    while num in M and not(num in common_lst):
      common_lst.append(num)
  return common_lst

##Examples:
check.expect("MarkUs Basic Test:", 
             intersect([2, 5, 5, 7, 9, 2, 4],
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
