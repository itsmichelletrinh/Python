````python
import check


def moving_average(L, k):
  '''
  Returns a list of the moving averages of k elements in L in O(n) time
  
  moving_average: (listof Nat) Nat -> (listof Float)
  Requires:
    k > 0
    
  Examples:
    moving_average([2183746932, 391284993304801], 1) => 
                   [2183746932.0, 391284993304801.0]
    moving_average([20, 18, 13, 16, 25, 22, 9], 2) =>
                   [19.0, 15.5, 14.5, 20.5, 23.5, 15.5]
    moving_average([], 1) => []
    moving_average([5, 10, 15, 20, 1, 2, 3], 3) => 
                   [10.0, 15.0, 12.0, 7.66667, 2.0]
  '''
  answer = []
  sums = sum(L[:k])
  
  if k > len(L):
    return answer
  else:
    for pos in range(len(L) - k + 1):
      answer.append(sums / k)
      if pos + k < len(L):
        sums += L[pos + k] - L[pos]
    return answer

##Examples:
check.within("MarkUs Basic Test", 
             moving_average([20, 18, 13, 16, 25, 22, 9], 2), 
             [19.0, 15.5, 14.5, 20.5, 23.5, 15.5], 0.00001)
check.within("Provided Example",
             moving_average([2183746932, 391284993304801], 1),
             [2183746932.0, 391284993304801.0], 0.00001)
check.within("Base Case", moving_average([], 1), [], 0.00001)
check.within("Personal Example",
             moving_average([5, 10, 15, 20, 1, 2, 3], 3),
             [10.0, 15.0, 12.0, 7.66667, 2.0], 0.00001)
             
##Tests:
check.within("L All 0s",
             moving_average([0, 0, 0, 0], 2), [0.0, 0.0, 0.0], 0.00001)
check.within("k > len(L)",
             moving_average([5, 10, 15, 20, 1, 2, 3], 10), [], 0.00001)
check.within("k = len(L)",
             moving_average([5, 10, 15, 20, 1, 2, 3], 7), [8.0], 0.00001)
````
