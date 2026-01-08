````python
import check


def restrict(source, maximums):
  '''
  Mutates source so that each number is smaller than or equal to the number at
  the same index in maximums 
  
  Effects: Mutates source 
  
  restrict: (listof Int) (listof Int) -> None
  Requires:
    len(source) == len(maximums)
  
  Examples: 
    L = []
    restrict(L, []) => None
    and L is unchanged 
  
    L = [3, 6, 0, -2, 4]
    restrict(L, [0, 10, 153250, 0, -10]) => None 
    and L is mutated to [0, 6, 0, -2, -10]
    
    L = [3, 6, 0, -2, 4]
    restrict(L, [0, 10, 116, 0, -10]) => None
    and L is mutated to [0, 6, 0, -2, -10]
    
    L = [1, 2, 3, 4]
    restrict(L, [3, 80, 50, 1]) => None
    and L is mutated to [1, 2, 3, 1]
  '''
  def mutate_from(source, maximums, pos):
    '''
    Mutates source so that each number is smaller than or equal to the number
    at the same index in maximums by mutating through each pos of source 
    
    Effects: Mutates source
    
    mutate_from: (listof Int) (listof Int) Nat -> (listof Int)
    '''
    if pos >= len(source):
      return None
    elif source[pos] <= maximums[pos]:
      mutate_from(source, maximums, pos+1)
    elif source[pos] > maximums[pos]:
      source[pos] = maximums[pos]
      mutate_from(source, maximums, pos+1)
  
  return mutate_from(source, maximums, 0)

##Examples:
L = [3, 6, 0, -2, 4]
check.expect("MarkUs Basic Test", restrict(L, [0, 10, 116, 0, -10]), None)
check.expect("MarkUs Basic Test Mutation", L, [0, 6, 0, -2, -10])

L = [3, 6, 0, -2, 4]
check.expect("Provided Example", restrict(L, [0, 10, 153250, 0, -10]), None)
check.expect("Provided Example Mutation", L, [0, 6, 0, -2, -10])

L = []
check.expect("Base Case", restrict(L, []), None)
check.expect("Base Case Mutation", L, [])

L = [1, 2, 3, 4]
check.expect("Personal Example", restrict(L, [3, 80, 50, 1]), None)
check.expect("Personal Example Mutation", L, [1, 2, 3, 1])

##Tests:
L = [1]
check.expect("Single Element", restrict(L, [5]), None)
check.expect("Single Element Mutation", L, [1])

L = [1, 1, 1]
check.expect("All L < Maximums", restrict(L, [5, 6, 7]), None)
check.expect("All L < Maximums Mutation", L, [1, 1, 1])

L = [100, 50, 2]
check.expect("All L > Maximums", restrict(L, [10, 5, 1]), None)
check.expect("All L > Maximums Mutation", L, [10, 5, 1])

L = [5, 10, 15]
check.expect("L == Maximums", restrict(L, [5, 10, 15]), None)
check.expect("L == Maximums Mutation", L, [5, 10, 15])
````
