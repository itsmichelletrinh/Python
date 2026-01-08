````python
import check


def create_grid(width, height, fill_value):
    '''
    Creates a 2D list of width lists of length height each 
    filled with the fill_value
    
    create_grid: Nat Nat Str -> (listof (listof Str))
    Requires:
       0 < width, height
    '''
    if height == 0:
        return []
    return [[fill_value] * width] + create_grid(width, height - 1, fill_value) 


def create_minesweeper_grid(width, height, mine_coordinates):
  '''
  Returns a minesweeper grid with width and height dimensions that contains 
  mines denoted by "X" at mine_coordinates where any cell not in the vicinity 
  of a mine is "" and cells in vicinity of mine(s) is "#" (the number of mines)
  in adjacent cells, including diagonals)
  
  create_minesweeper_grid: Nat Nat (listof (listof Nat Nat)) -> 
                           (listof (listof Str))
  Requires:
    width, height > 0 
    mine_coordinates are distinct and within grid
    
  Examples:
    create_minesweeper_grid(1, 1, [[0,0]]) => 
                           [["X"]]
                           
    create_minesweeper_grid(1, 1, []) => 
                           [[""]]
                           
    create_minesweeper_grid(2, 2, [[0,0], [1,1]]) =>
                           [["X", "2"],
                           ["2", "X"]]
                           
    create_minesweeper_grid(5, 3, [[1,1], [2,2], [1,2]]) => 
                           [["1", "2", "2", "1", ""],
                           ["1", "X", "X", "2", ""],
                           ["1", "3", "X", "2", ""]]
  '''
  grid = create_grid(width, height, "") # Base Grid With Proper Dimensions 
  
  def add_mines(grid, mine_coordinates, pos):
    '''
    Returns a grid with mines ("X") added at each mine_coordinates by 
    going through each pos of mine_coordinates 
    
    add_mines: (listof (listof Str)) (listof (listof Nat Nat)) Nat -> 
               (listof (listof Str))
    '''
    if pos >= len(mine_coordinates):
      return grid
    
    row = mine_coordinates[pos][0]
    column = mine_coordinates[pos][1]
    grid[row][column] = "X"  
    
    return add_mines(grid, mine_coordinates, pos+1)
    
    
  grid_with_mines = add_mines(grid, mine_coordinates, 0) # Grid With Mines
  
  def count_mines(grid, row, column):
    '''
    Returns the total number of mines in the vicinity of a given row and column
    in grid or "" if there are no mines in vicinity 
    
    count_mines: (listof (listof Str)) Nat Nat -> Str
    '''
    def is_valid(row, column):
      '''
      Returns True if row and column are valid such that they are within grid
      
      is_valid: Nat Nat -> Bool
      '''
      return 0 <= row < len(grid) and 0 <= column < len(grid[0])
      
      
    directions = [(-1, -1), (-1, 0), (-1, 1), 
                  (0, -1),           (0, 1), 
                  (1, -1), (1, 0), (1, 1)]  
    
    def count_in_direction(pos):
      '''
      Returns the total number of mines found by checking through valid pos of 
      eight different directions
      
      count_in_direction: Nat -> Nat
      '''
      if pos >= len(directions):
        return 0
      dr = directions[pos][0]
      dc = directions[pos][1]
      new_row = row + dr
      new_column = column + dc
      if is_valid(new_row, new_column) and grid[new_row][new_column] == "X":
        return 1 + count_in_direction(pos+1)
      return count_in_direction(pos+1)
    
    
    mine_count = count_in_direction(0)
    
    if mine_count > 0:
      return str(mine_count)
    return ""
    
    
  def add_num(grid, row, column):
    '''
    Returns a grid with numbers that represent the total number of mines in 
    vicinity to that cell by updating each row and column in grid 
    
    add_num: (listof (listof Str)) Nat Nat -> (listof (listof Str))
    '''
    if row >= len(grid):
      return grid
    elif column >= len(grid[row]):
      return add_num(grid, row+1, 0)
    else:
      if grid[row][column] != "X":
        grid[row][column] = count_mines(grid, row, column)
      return add_num(grid, row, column+1)
  
  return add_num(grid_with_mines, 0, 0)
  
##Examples:
check.expect("MarkUs Basic Test", 
             create_minesweeper_grid(5, 3, [[1,1], [2,2], [1,2]]),
             [["1", "2", "2", "1", ""],
              ["1", "X", "X", "2", ""],
              ["1", "3", "X", "2", ""]])
              
check.expect("Base Case #1, Smallest Grid & 1 Mine",
             create_minesweeper_grid(1, 1, [[0,0]]), 
             [["X"]])
             
check.expect("Base Case #2, Smallest Grid & No Mines",
             create_minesweeper_grid(1, 1, []),
             [[""]])

check.expect("Personal Example",
             create_minesweeper_grid(2, 2, [[0,0], [1,1]]),
             [["X", "2"],
             ["2", "X"]])

##Tests:
check.expect("Surrounded By Mines",
             create_minesweeper_grid(3, 3, [[0,0], [0,1], [0,2], [1,0], [1,2], 
                                     [2,0], [2,1], [2,2]]),
             [["X", "X", "X"],
             ["X", "8", "X"],
             ["X", "X", "X"]])
             
check.expect("No Mines",
             create_minesweeper_grid(3, 3, []),
             [["", "", ""],
             ["", "", ""],
             ["", "", ""]])
             
check.expect("All Mines",
             create_minesweeper_grid(2, 2, [[0,0], [0,1], [1,0], [1,1]]),
             [["X", "X"],
             ["X", "X"]])
````
