````python
import check
import math


#Constants
max_pizza_slices = 8

def how_many_pizzas(slices_veg, slices_meat, slices_deluxe):
  '''
  Returns the minimum number of pizzas to order based on the number of slices
  of slices_veg, slices_meat, and slices_deluxe
  
  how_many_pizzas: Nat Nat Nat -> Nat
  
  Examples:
    how_many_pizzas(3, 16, 435024) => 54381 
  '''  
  return math.ceil((slices_veg / max_pizza_slices) + (slices_meat / 
         max_pizza_slices) + (slices_deluxe / max_pizza_slices))

##Examples:
check.expect("Example #1, generic case", how_many_pizzas(3, 16, 435024), 54381)

##Tests:
check.expect("MarkUs Basic Test",how_many_pizzas(3, 16, 0), 3)
check.expect("Example #1", how_many_pizzas(3, 16, 435024), 54381)
check.expect("One 0 value", how_many_pizzas(0, 16, 16), 4)
check.expect("All 0 values", how_many_pizzas(0, 0, 0), 0)
check.expect("Large values", how_many_pizzas(250000, 500000, 1000), 93875)
````
