## Aim
To perform Depth First Search (DFS) traversal on a graph starting from a given source vertex using recursion.

## Algorithm
1. Mark the current vertex as visited
2. Print the current vertex
3. Recursively visit all adjacent unvisited vertices
4. Repeat until all reachable vertices are visited

## Program
```python
class Graph:
    def __init__(self, vertices):
        self.V = vertices
        self.graph = [[] for _ in range(vertices)]
    
    def add_edge(self, u, v):
        self.graph[u].append(v)
    
    def DFSUtil(self, v, visited):
        visited[v] = True
        print(v, end=' ')
        
        for i in self.graph[v]:
            if not visited[i]:
                self.DFSUtil(i, visited)
    
    def DFS(self, v):
        visited = [False] * self.V
        print("Following is DFS from (starting from vertex", v, ")")
        self.DFSUtil(v, visited)
        print()

g = Graph(4)
g.add_edge(0, 1)
g.add_edge(0, 2)
g.add_edge(1, 2)
g.add_edge(2, 0)
g.add_edge(2, 3)
g.add_edge(3, 3)

v = int(input())
g.DFS(v)
```

## Output
```
Input: 2
Following is DFS from (starting from vertex 2)
2 0 1 3

Input: 1
Following is DFS from (starting from vertex 1)
1 2 0 3
```
