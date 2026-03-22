## Aim
To perform topological sorting on a Directed Acyclic Graph (DAG) using Kahn's algorithm (BFS-based approach) and display the vertices in topological order.

## Algorithm
1. Calculate in-degree (number of incoming edges) for each vertex
2. Initialize a queue with all vertices having in-degree 0
3. While queue is not empty:
   - Remove a vertex from queue and add to result
   - Decrease in-degree of all its neighbors by 1
   - If any neighbor's in-degree becomes 0, add to queue
4. Output the result list (topological order)

## Program
```python
from collections import defaultdict, deque

class Graph:
    def __init__(self, vertices):
        self.graph = defaultdict(list)
        self.V = vertices
    
    def add_edge(self, u, v):
        self.graph[u].append(v)
    
    def topological_sort(self):
        in_degree = [0] * self.V
        
        for i in self.graph:
            for j in self.graph[i]:
                in_degree[j] += 1
        
        queue = deque()
        for i in range(self.V):
            if in_degree[i] == 0:
                queue.append(i)
        
        result = []
        while queue:
            u = queue.popleft()
            result.append(u)
            
            for i in self.graph[u]:
                in_degree[i] -= 1
                if in_degree[i] == 0:
                    queue.append(i)
        
        return result

g = Graph(6)
g.add_edge(5, 2)
g.add_edge(5, 0)
g.add_edge(4, 0)
g.add_edge(4, 1)
g.add_edge(2, 3)
g.add_edge(3, 1)

print("Topological Sort of the given graph is")
print(' '.join(map(str, g.topological_sort())))
```

## Output
```
Topological Sort of the given graph is
5 4 2 3 1 0
```
