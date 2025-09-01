# EX 2B BACKTRACKING - NQUEEN PROBLEM

## DATE: 05-05-2025

## AIM:

To solve the N-Queen problem using backtracking, which places N queens on an N\*N chessboard such that no two queens threaten each other.

## Algorithm

1. Initialize an N x N board with all zeros.
2. Try placing a queen in each column, one by one.
3. For each placement, check if it's safe (no queen in the same row, column, or diagonal).
4. If safe, recursively attempt to place queens in the next column.
5. If all queens are placed successfully, print the solution; otherwise, backtrack and try the next possibility.

## Program:

```python
# Program to implement N-Queen problem using backtracking.


global N
N = int(input())

def printSolution(board):
    for i in range(N):
        for j in range(N):
            print(board[i][j], end = " ")
        print()

def isSafe(board, row, col):

    # Check this row on left side
    for i in range(col):
        if board[row][i] == 1:
            return False

    # Check upper diagonal on left side
    for i, j in zip(range(row, -1, -1),
                    range(col, -1, -1)):
        if board[i][j] == 1:
            return False

    # Check lower diagonal on left side
    for i, j in zip(range(row, N, 1),
                    range(col, -1, -1)):
        if board[i][j] == 1:
            return False

    return True

def solveNQUtil(board, col):
    if col>=N:
        return True

    for i in range(N):
        if isSafe(board,i,col):
            board[i][col] = 1
            if solveNQUtil(board, col+1):
                return True
            board[i][col]=0
    return False

def solveNQ():
    board = [ [0, 0, 0, 0],
              [0, 0, 0, 0],
              [0, 0, 0, 0],
              [0, 0, 0, 0]]

    if solveNQUtil(board, 0) == False:
        print ("Solution does not exist")
        return False

    printSolution(board)
    return True

# Driver Code
solveNQ()
```

## Output:

<img width="1171" height="371" alt="image" src="https://github.com/user-attachments/assets/93394ef0-0a85-47af-9cbd-9c17e887ae41" />

## Result:

The N-Queens program executed successfully, and a valid board configuration was generated.
