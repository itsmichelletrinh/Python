````python
import check


def intersect(source, others):
  '''
  Mutates source to only the numbers that are also in every lists in others
  
  Effects: Mutates source
  
  intersect: (listof Int) (listof (listof Int)) -> None
  
  Examples:
    source = [1, 4, 6, 2, 1, 677196]
    others = [[4, 1], [6, 9, 1, 4], [0, 2, 2, 2, 4, 2, 1]]
    intersect(source, others) => None
    and source is mutated to [1, 4, 1]
    
    intersect([], []) => None
    and source is unchanged
    
    intersect([], [[1, 2], [1]]) => None
    and source is unchanged
    
    intersect([1, 2, 3], [[]]) => None
    and source is mutated to []
    
    source = [1, 2, 3, 4, 5]
    others = [[1, 2], [10, 1, 9], [3, 1], [1]]
    intersect(source, others) => None
    and source is mutated to [1]
  '''
  remove_num = [] #List of #s to remove from source 
  for num in source:  #Determines which #s to remove from source
    for lst in others:
      if not(num in lst) and not(num in remove_num):
        remove_num.append(num)  
  
  pos = 0   #Removes #s from source 
  while pos < len(source):
    if source[pos] in remove_num:
      source.remove(source[pos])
    else:
      pos += 1
      
##Examples:
source = [1, 4, 6, 2, 1]
others = [[4, 1], [6, 9, 1, 4], [0, 2, 2, 2, 4, 2, 1]]
check.expect("MarkUs Basic Test", intersect(source, others), None)
check.expect("MarkUs Basic Test Mutation", source, [1, 4, 1])

check.expect("Base Case, Both Empty", intersect([], []), None)
check.expect("Base Case Mutation", [], [])

check.expect("Source Empty", intersect([], [[1, 2], [1]]), None)
check.expect("Source Empty Mutation", [], [])

check.expect("Others 1 Empty List", intersect([1, 2, 3], [[]]), None)
check.expect("Others 1 Empty List Mutation", [1, 2, 3], [])

source = [1, 2, 3, 4, 5]
others = [[1, 2], [10, 1, 9], [3, 1], [1]]
check.expect("Personal Example", intersect(source, others), None)
check.expect("Personal Example Mutation", source, [1])

##Tests:
source = [1, 2, 3, 4, 5]
others = [[1, 2], [3, 4], [5, 6]]
check.expect("No Numbers In All Lists", intersect(source, others), None)
check.expect("No Numbers In All Lists Mutation", source, [])

source = [1, 10, 9, 1, 5, 2, 1, 7]
others = [[1, 2], [3, 1, 4], [5, 1, 6]]
check.expect("Multiple Same #s", intersect(source, others), None)
check.expect("Multiple Same #s Mutation", source, [1, 1, 1])
````
