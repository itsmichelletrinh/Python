````python
import check


#Constants
correct_prompt = "Correct!"
game_over_prompt = "I'm sorry, the number was {0}"
higher_prompt = "Higher"
lower_prompt = "Lower"

def guessing_game(hidden, num_guesses):
  '''
  Prints one of four responses based on a user's input from keyboard that 
  matches or mismatches hidden and the user's number of guesses tracked in 
  num_guesses
  
  Effects: 
    Prints to screen
    Reads input from keyboard
  
  guessing_game: Int Nat -> None 
  Requires:
    1 <= hidden <= 100
    num_guesses > 0
  
  Examples:
    If we call 
    guessing_game(42, 3) => None 
    and give integers 50, 25, 38 as input,
    we print "Lower", "Higher", "I'm sorry, the number was 42" to the screen 
    (no quotes) on separate lines 
           
    If we call
    guessing_game(42, 439944) => None 
    and give integer 42 as input,
    we print "Correct!" to the screen (no quotes)
    
    If we call 
    guessing_game(6, 2) => None 
    and give integer 2, 6 as input,
    we print "Higher", "Correct!" to the screen (no quotes) on separate lines
  '''
  guess = int(input())
  if guess == hidden:
    print(correct_prompt)
  elif (guess != hidden) and (num_guesses == 1):
    print(game_over_prompt.format(hidden))
  elif (guess > hidden) and (num_guesses > 1):
    print(lower_prompt)
    return guessing_game(hidden, num_guesses - 1)
  elif (guess < hidden) and (num_guesses > 1):
    print(higher_prompt)
    return guessing_game(hidden, num_guesses - 1)
    
##Examples:
check.set_print_exact("Lower", "Higher", "I'm sorry, the number was 42")
check.set_input('50', '25', '38')
check.expect('MarkUs Basic Test', guessing_game(42, 3), None)

check.set_print_exact("Correct!")
check.set_input("42")
check.expect("Base Case", guessing_game(42, 439944), None)

check.set_print_exact("Higher", "Correct!")
check.set_input("2", "6")
check.expect("Basic Example", guessing_game(6, 2), None)

##Tests:
check.set_print_exact("I'm sorry, the number was 6")
check.set_input("10")
check.expect("Incorrect One Guess", guessing_game(6, 1), None)
````
