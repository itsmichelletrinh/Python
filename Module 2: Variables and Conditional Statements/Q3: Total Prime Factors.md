````python
import check


def is_composite_2_to_d(n,d):
  '''
  Returns True if any number between 2 and d divides n and False otherwise 
  Code used from Concept Check 2.4.3
  
  is_composite_2_to_d: Nat Nat -> Bool
  Requires:
    2 <= n
    1 <= d <= n-1
  '''  
  if d == 1:
    return False
  elif (n % d == 0 or is_composite_2_to_d(n, d-1)):
    return True
  else:
    return False 
    

def is_prime(n):
  '''
  Returns True if n is prime and False otherwise
  Code used from Concept Check 2.4.4
  
  is_prime: Nat -> Bool
  '''
  if n - 1 == 0:
    return False
  elif is_composite_2_to_d(n, n-1) == True:
    return False
  else:
    return True 


def total_prime_factors(n):
  '''
  Returns the total number of prime factors of n 
  
  total_prime_factors: Nat -> Nat 
  Requires: 
    n > 0
  
  Examples: 
    total_prime_factors(3) => 1 
    total_prime_factors(10) => 2 
  '''
  def count_prime_factors(n, divisor):
    '''
    Returns the number of prime factors of n by dividing it by prime divisors 
    
    count_prime_factors: Nat -> Nat 
    '''
    if n == 1:
      return 0
    elif n % divisor == 0:
      return 1 + count_prime_factors(n // divisor, divisor)
    else:
      return count_prime_factors(n, divisor + 1)
      
  if n <= 1:
    return 0
  elif is_prime(n):
    return 1
  else:
    return count_prime_factors(n,2)

##Examples:
check.expect("MarkUs Basic Test", total_prime_factors(10), 2)
check.expect("Example", total_prime_factors(3), 1)
check.expect("Base Case", total_prime_factors(1), 0)

##Tests:
check.expect("n Is Prime Number", total_prime_factors(2), 1)
check.expect("Duplicate Prime Factors", total_prime_factors(4), 1)
````
