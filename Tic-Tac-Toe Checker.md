# Tic-Tac-Toe Checker [5 kyu]

[See Problem] (https://www.codewars.com/kata/525caa5c1bf619d28c000335)


If we were to set up a Tic-Tac-Toe game, we would want to know whether the board's current state is solved, wouldn't we? Our goal is to create a function that will check that for us!

Assume that the board comes in the form of a 3x3 array, where the value is `0` if a spot is empty, `1` if it is an "X", or `2` if it is an "O", like so:
```
[[0, 0, 1],
 [0, 1, 2],
 [2, 1, 0]]
```
We want our function to return:

- `-1` if the board is not yet finished AND no one has won yet (there are empty spots),
- `1` if "X" won,
- `2` if "O" won,
- `0` if it's a cat's game (i.e. a draw).

You may assume that the board passed in is valid in the context of a game of Tic-Tac-Toe.

## Solution

```
def is_solved(board):
    #Check line
    if [1,1,1] in board:
        return 1
    if [2,2,2] in board:
        return 2
    
    #Check column
    columns = [[line[x] for line in board] for x in range(3)]
    if [1,1,1] in columns:
        return 1
    if [2,2,2] in columns:
        return 2
    
    #Diagonal right
    diagonal_right = [board[x][2-x] for x in range(3)]
    if diagonal_right == [1,1,1]:
        return 1
    if diagonal_right == [2,2,2]:
        return 2
    
    #Diagonal left
    diagonal_left = [board[x][x] for x in range(3)]
    if diagonal_left == [1,1,1]:
        return 1
    if diagonal_left == [2,2,2]:
        return 2
    
    if all([all(line) for line in board]):
        return 0
    
    return -1
```