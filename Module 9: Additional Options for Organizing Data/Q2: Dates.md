````python
import check


def is_leap_year(year):
  '''
  Returns True if year is a leap year, else False.
  
  is_leap_year: Nat -> Bool
  Requires: year >= 1800
  '''
  return (year % 4 == 0 and 
         (year % 100 != 0 or year % 400 == 0))

class Date:
  '''
  Fields: 
    day (Nat)
    month (Nat)
    year (Nat)
      
  Requires: 
    year >= 1800
    day month year corresponds to a valid date
      in the Gregorian Calendar
  '''
   
  def __init__(self, d, m, y):
    '''
    Constructor: Create a Date object by calling Date(d, m, y)
    
    Effects: Mutates self
    
    __init__: Date Nat Nat Nat -> None
    Requires: 1 <= d <= 31, 1 <= m <= 12, year >= 1800
    '''
    self.day = d
    self.month = m
    self.year = y
	 
  def __repr__(self):
    '''
    Returns a string representation of self
    
    __repr__: Date -> Str
    '''
    s = "Date({0.day},{0.month},{0.year})"
    return s.format(self)
	 
  def __eq__(self, other):
    '''
    Returns True if self and other are considered equal, and False otherwise
    
    __eq__: Date Any -> Bool
    '''
    return isinstance(other, Date) and\
           self.day == other.day and\
           self.month == other.month and\
           self.year == other.year

  def add_days(self, n):
    '''
    Returns a new Date that is n days after self
    
    add_days: Date Nat -> Date
    Requires: 
      n > 0
  
    Examples: 
      add_days(Date(6,7,2020), 30) => Date(5,8,2020)
      add_days(Date(6,7,2020), 1) => Date(7,7,2020)
      add_days(Date(6,10,2002), 30) => Date(5,11,2002)
    '''
    new_date = Date(self.day + n, self.month, self.year)
    
    while new_date.day > 28:
      if new_date.month in [4, 6, 9, 11] and new_date.day > 30:
        new_date.day -= 30
        new_date.month += 1
            
      elif new_date.month in [1, 3, 5, 7, 8, 10, 12] and new_date.day > 31:
        new_date.day -= 31
        new_date.month += 1
                
      elif is_leap_year(new_date.year) and new_date.day > 29:
        new_date.day -= 29
        new_date.month += 1
            
      elif not is_leap_year(new_date.year) and new_date.day > 28:
        new_date.day -= 28
        new_date.month += 1
        
      if new_date.month > 12:
        new_date.month -= 12
        new_date.year += 1
        
    return new_date

##Testing __init__
d = Date(1,2,2000)
check.expect("Markus Basic Test 0 day", d.day, 1)
check.expect("Markus Basic Test 0 month", d.month, 2)
check.expect("Markus Basic Test 0 year", d.year, 2000)

##Testing __repr__
check.expect("Markus Basic Test 1", str(Date(1,1,2000)), "Date(1,1,2000)")

##Testing __eq__
check.expect("Markus Basic Test 2", Date(1,1,2000) == Date(1,1,2000), True)
check.expect("False", Date(1,1,2000) == Date(1,2,2000), False)

##Examples for add_days
check.expect("Markus Basic Test 3", Date(6,7,2020).add_days(30), Date(5,8,2020))
check.expect("Base Case, n = 1", Date(6,7,2020).add_days(1), Date(7,7,2020))
check.expect("Personal Example", Date(6,10,2002).add_days(30), Date(5,11,2002))

##Tests for add_days
check.expect("30-Day Month", Date(6,9,2020).add_days(30), Date(6,10,2020))
check.expect("Leap Year Feb", Date(6,2,2020).add_days(30), Date(7,3,2020))
check.expect("Non-Leap Year Feb", Date(6,2,2023).add_days(30), Date(8,3,2023))
check.expect("New Year", Date(6,12,2023).add_days(30), Date(5,1,2024))
check.expect("Multiple Months", Date(6,1,2023).add_days(100), Date(16,4,2023))
check.expect("n = 365", Date(6,10,2002).add_days(365), Date(6,10,2003))
````
