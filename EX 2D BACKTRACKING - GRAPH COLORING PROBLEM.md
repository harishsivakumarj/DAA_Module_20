# EX 2D BACKTRACKING - GRAPH COLORING PROBLEM

## DATE: 05-05-2025

## AIM:

To solve the Graph Coloring Problem using backtracking, assigning colors to the vertices of a graph such that no two adjacent vertices share the same color while minimizing the number of colors used.

## Algorithm

1. Initialize a graph with V vertices and a 2D adjacency matrix.

2. For each vertex, check if it's safe to assign a color using isSafe function (no adjacent vertex has the same color).

3. Recursively try assigning colors to vertices, starting from the first vertex.

4. If all vertices are successfully colored, return True and print the assigned colors.

5. If no valid coloring exists, backtrack and print "No solution exists".

## Program:

```python
# Program to implement Graph Coloring Problem using backtracking.

class Graph:
    def __init__(self,vertices):
        self.V=vertices
        self.Graph=[[0 for column in range(vertices)]for row in range(vertices)]
    def isSafe(self,v,colour,c):
        for i in range(self.V):
            if self.graph[v][i]==1 and colour[i]==c:
                return False
        return True
    def graphColourUtil(self,m,colour,v):
        if v==self.V:
            return True
        for c in range(1,m+1):
            if self.isSafe(v,colour,c):
                colour[v]=c
                if self.graphColourUtil(m,colour,v+1):
                    return True
                colour[v]=c
        return False
    def graphColouring(self,m):
        colour=[0]*self.V
        if not self.graphColourUtil(m,colour,0):
            print("No solution Exist")
            return False
        print("Solution exist and Following are the assigned colours:")
        for c in colour:
            print(c,end=' ')
        print()
        return True
```

## Output:

<img width="1129" height="150" alt="image" src="https://github.com/user-attachments/assets/a854a207-693c-4cb6-bd27-55dcfe2b689b" />

## Result:

The Graph Coloring program executed successfully, and the colors were assigned to the vertices such that no two adjacent vertices share the same color.
