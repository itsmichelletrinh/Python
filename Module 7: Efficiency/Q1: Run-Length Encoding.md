````python
import check


def rl_encode(s):
  '''
  Returns the run-length encoding in O(n) time of the string s 
  
  rl_encode: Str -> Str 
  Requires: 
    s has no spaces 
    
  Examples:
    rl_encode("aaabbabbbbbbbbbbb") => "3a 2b 1a 11b"
    rl_encode('abbbbbaaaaaaaaaabbbbbaaaa') => "1a 5b 10a 5b 4a"
    rl_encode("aa") => "2a"
    rl_encode("a") => "1a"
  '''
  blocks = []
  current_block = ""
  
  for char in s:
    if current_block == "" or char == current_block[-1]:
      current_block += char 
    else:
      blocks.append(current_block)
      current_block = char 
  if current_block != "":
    blocks.append(current_block)
    
  answer = ""
  
  for block in blocks:
    answer += str(len(block)) + block[0] + " "
  return answer.strip()

##Examples:
check.expect("MarkUs Basic Test", 
             rl_encode("aaabbabbbbbbbbbbb"), "3a 2b 1a 11b")
check.expect("Provided Example #1",
             rl_encode('abbbbbaaaaaaaaaabbbbbaaaa'), "1a 5b 10a 5b 4a")
check.expect("Provided Example #2",
             rl_encode("aa"), "2a")
check.expect("Base Case", rl_encode("a"), "1a")
             
##Tests:
check.expect("Mixed Characters",
             rl_encode("d3733888dHa!"), "1d 13 17 23 38 1d 1H 1a 1!")
````
