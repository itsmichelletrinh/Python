````python
import check


#Constants
prompt = "Player {0}'s hand: "
score_message = "Player 1: {0}, Player 2: {1}"
tie_message = "Tie!"
win_message = "Player {0} wins!"
error_message = "Error. Not a valid option."
rock = "rock"
paper = "paper"
scissors = "scissors"

def ro_sham_bo(total_winning_throws):
  '''
  Prints the current status of the game, including an error message when player 
  inputs from keyboard are not valid, scores, and whether inputs tied or a 
  player has won when a player reaches a total total_winning_throws won games
  
  Effects:
    Prints to screen
    Reads input from keyboard
    
  ro_sham_bo: Nat
  Requires:
    total_winning_throws > 0
    
  Examples:
    If we call 
    ro_sham_bo(2) => None
    and give paper, scissors, 0000000, scissors, scissors, rock, scissors, rock,
    paper as input, 
    we print "Player 1: 0, Player 2: 1", "Error. Not a valid option.", "Tie!",
    "Player 1: 0, Player 2: 1", "Player 1: 1, Player 2: 1", "Player 2 wins!" to
    the screen (no quotes) on separate lines
    
    If we call
    ro_sham_bo(1) => None 
    and give paper, scissors as input,
    we print "Player 2 wins!" to the screen (no quotes) on separate lines
    
    If we call
    ro_sham_bo(2) => None
    and give paper, paper, rock, scissors, paper, rock as input,
    we print "Tie!", "Error. Not a valid option.", "Player 1: 1, Player 2: 0", 
    "Player 1 wins!" to the screen (no quotes) on separate lines 

  '''
  p1_score = 0
  p2_score = 0
  
  while p1_score < total_winning_throws and p2_score < total_winning_throws:
    p1_shape = input(prompt.format(1))
    p2_shape = input(prompt.format(2))
    
    if p1_shape in [rock, paper, scissors] and \
       p2_shape in [rock, paper, scissors]:
         
      if p1_shape == p2_shape:
        print(tie_message)
        print(score_message.format(p1_score, p2_score))
        
      elif (p1_shape == rock and p2_shape == scissors) or (p1_shape == paper
          and p2_shape == rock) or (p1_shape == scissors and p2_shape == paper):
        p1_score += 1
        print(score_message.format(p1_score, p2_score))
        
      else:
        p2_score += 1
        print(score_message.format(p1_score, p2_score))
        
    else:
      print(error_message)
      if not(p1_shape in [rock, paper, scissors]):
        p1_shape = input(prompt.format(1))
      else:
        p2_shape = input(prompt.format(2))
  
  if p1_score > p2_score:
    print(win_message.format(1))
  print(win_message.format(2))

##Examples:
check.set_input("paper", "scissors", "0000000", "scissors", "scissors", "rock",
                "scissors", "rock", "paper")
check.set_print_exact("Player 1: 0, Player 2: 1", "Error. Not a valid option.",
                      "Tie!", "Player 1: 0, Player 2: 1", 
                      "Player 1: 1, Player 2: 1", "Player 2 wins!")
check.expect("MarkUs Basic Test", ro_sham_bo(2), None)

check.set_input("paper", "scissors")
check.set_print_exact("Player 2 wins!")
check.expect("Base Case", ro_sham_bo(1), None)

check.set_input("paper", "paper", "rock", "scissors", "paper", "rock")
check.set_print_exact("Tie!", "Player 1: 0, Player 2: 0", 
                      "Player 1: 1, Player 2: 0", "Player 1 Wins!")
check.expect("Personal Example", ro_sham_bo(2), None)

##Tests:
check.set_input("paper", "paper", "hi", "hello", "rock", "scissors", "paper", 
                "rock")
check.set_print_exact("Tie!", "Player 1: 0, Player 2: 0", 
                      "Error. Not a valid option.", "Error. Not a valid option.",
                      "Player 1: 1, Player 2: 0", "Player 1 Wins!")
check.expect("Consecutive Errors", ro_sham_bo(2), None)
````
