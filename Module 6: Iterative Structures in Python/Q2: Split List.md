````python
import check


def split_list(source, partition_size):
  '''
  Returns a list of lists containing all elements of source split amongst lists
  of partition_size elements, except the last one that might be smaller
  
  split_list: (listof Int) Nat -> (listof (listof Int))
  Requires:
    partition_size > 0
  
  Examples:
    split_list([1, 2, 3, 4, 5, 6, 7, 8, 9], 4) => 
              [[1, 2, 3, 4], [5, 6, 7, 8], [9]]
    split_list([], 49924312) => []
    split_list([], 1) => []
    split_list([6, 10, 2, 7, 8], 2) => [[6, 10], [2, 7], [8]]
  '''
  lol = []
  sublist = []
  
  for num in source:
    sublist.append(num)
    if len(sublist) == partition_size:
      lol.append(sublist)
      sublist = []
  if len(sublist) > 0:
    lol.append(sublist)
  return lol
    
##Examples:
check.expect("MarkUs Basic Test",
             split_list([1, 2, 3, 4, 5, 6, 7, 8, 9], 4),
             [[1, 2, 3, 4], [5, 6, 7, 8], [9]])
check.expect("Provided Example", split_list([], 49924312), [])
check.expect("Base Case", split_list([], 1), [])
check.expect("Personal Example", split_list([6, 10, 2, 7, 8], 2), 
             [[6, 10], [2, 7], [8]])
             
##Tests:
check.expect("Partition Size > len(source)", split_list([1, 2], 5), [[1, 2]])
check.expect("Smallest Partition Size", split_list([1, 2, 3, 4, 5], 1),
             [[1], [2], [3], [4], [5]])
````
