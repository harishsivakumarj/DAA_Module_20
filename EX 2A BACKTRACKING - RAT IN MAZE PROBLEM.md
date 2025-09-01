# EX 2A BACKTRACKING - RAT IN MAZE PROBLEM

## DATE: 29-04-2025

## AIM:

To implement the Rat in a Maze problem using backtracking and find all possible paths from the start to the destination in a given maze.

## Algorithm

1. Initialize a solution matrix with zeros.
2. Start at the top-left corner and recursively explore possible paths.
3. Check if moving to a cell is safe (within bounds and open).
4. If reaching the bottom-right corner, mark the cell as part of the path.
5. If a path is found, print the solution matrix; otherwise, backtrack and return "Solution doesn't exist."

## Program:

```python
# Program to implement Rat in a Maze.


N = 4

def printSolution(sol):
    for i in sol:
        for j in i:
            print(str(j) + " ", end="")
        print("")

def isSafe(maze, x, y):
    return x >= 0 and x < N and y >= 0 and y < N and maze[x][y] == 1

def solveMaze(maze):
    sol = [[0 for _ in range(N)] for _ in range(N)]

    if not solveMazeUtil(maze, 0, 0, sol):
        print("Solution doesn't exist")
        return False

    printSolution(sol)
    return True

def solveMazeUtil(maze, x, y, sol):
    # If (x, y) is the destination, return true
    if x == N - 1 and y == N - 1:
        sol[x][y] = 1
        return True

    if isSafe(maze, x, y):
        sol[x][y] = 1  # Mark as part of the solution path

        # Move right
        if solveMazeUtil(maze, x, y + 1, sol):
            return True

        # Move down
        if solveMazeUtil(maze, x + 1, y, sol):
            return True

        sol[x][y] = 0  # Backtrack

    return False

if __name__ == "__main__":
    maze = [[1, 0, 0, 0],
            [1, 1, 0, 1],
            [0, 1, 0, 0],
            [1, 1, 1, 1]]

    solveMaze(maze)
```

## Output:
<img width="441" height="271" alt="image" src="https://github.com/user-attachments/assets/c1b007ba-ad2c-4e9f-a3fb-8f836a5fdfce" />

## Result:

The Rat in a Maze program executed successfully, and a valid path from the start to the destination was found and display.
