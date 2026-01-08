````python
import check


def harmonic(n):
  '''
  Returns the nth harmonic number 
  
  harmonic: Nat -> Float 
  Requires:
    n > 0
  
  Examples:
    harmonic(3) => 1.8333333
    harmonic(2) => 1.5
    harmonic(1) => 1.0
  '''
  if n == 1:
    return 1.0
  return 1/n + harmonic(n-1)

##Examples:
check.within("Provided Example", harmonic(3), 1.8333333, 0.00001)
check.within("Generic Recursive Case", harmonic(2), 1.5, 0.00001)
check.within("Base Case", harmonic(1), 1.0, 0.00001)

##Tests:
check.within("Slightly Larger n", harmonic(10), 2.92897, 0.00001)
````
