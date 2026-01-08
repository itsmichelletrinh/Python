````python
import check


def largest_edge_group(vertices):
  '''
  Returns the size of the largest group of the same length edges from a simple
  polygon formed by vertices 
  
  largest_edge_group: (listof (listof Int)) -> Nat
  
  Examples:
    largest_edge_group([[0,0],[1,1],[0,2],[-2,3],[-1,2],[-533849,-533849]]) => 3
    largest_edge_group([[0,0],[1,1],[0,2],[-2,3],[-1,2]]) => 3
    largest_edge_group([[0,0],[2,0],[2,3],[1,4],[0,3]]) => 2
    largest_edge_group([[2,3], [-1,5], [4,-2]]) => 1
  '''
  side_lengths = {}
  
  for pos in range(len(vertices)):
    if pos < len(vertices)-1:
      length = (vertices[pos][0] - vertices[pos+1][0])**2 + \
               (vertices[pos][1] - vertices[pos+1][1])**2
    else:
      length = (vertices[pos][0] - vertices[0][0])**2 + \
               (vertices[pos][1] - vertices[0][1])**2
  
    if length in side_lengths:
      side_lengths[length] += 1
    else:
      side_lengths[length] = 1
  return max(list(side_lengths.values()))

##Examples:
check.expect("MarkUs Basic Test",
             largest_edge_group([[0, 0], [1, 1], [0, 2], [-2, 3], [-1, 2]]), 3)
check.expect("Provided Example", largest_edge_group(
             [[0,0],[1,1],[0,2],[-2,3],[-1,2],[-533849,-533849]]), 3)
check.expect("Personal Example", largest_edge_group(
             [[0,0],[2,0],[2,3],[1,4],[0,3]]), 2)
check.expect("Base Case, 3 Vertices", largest_edge_group(
             [[2,3], [-1,5], [4,-2]]), 1)
             
##Tests:
check.expect("No Sides Equal", largest_edge_group(
             [[60, 10], [10, 10], [40,-15], [60, -15]]), 1)
check.expect("All Sides Equal", largest_edge_group(
             [[0,0], [0,4], [4,4], [4,0]]), 4)
````
