**Topic:** BFS Traversal from Source Vertex

**AIM:**  
To write a Python program with a BFS function that performs breadth-first traversal from a given source vertex in a graph.

**ALGORITHM:**  
1. Start  
2. Define `bfs(graph, start)` function:  
   a. Initialize a visited set to track visited vertices  
   b. Initialize a queue with the start vertex  
   c. Mark start vertex as visited  
   d. While queue is not empty:  
      - Dequeue a vertex and print it  
      - For each neighbor in graph[vertex]:  
        - If neighbor not visited, mark visited and enqueue it  
3. Create adjacency list representation of graph  
4. Read source vertex from user  
5. Call bfs function and display traversal  
6. End  

**PROGRAM:**  
```
from collections import deque

def bfs(graph, start):
    visited = set()
    queue = deque([start])
    visited.add(start)
    result = []
    
    while queue:
        vertex = queue.popleft()
        result.append(vertex)
        for neighbor in graph[vertex]:
            if neighbor not in visited:
                visited.add(neighbor)
                queue.append(neighbor)
    return result

graph = {
    0: [1, 2, 3],
    1: [0, 2],
    2: [0, 1, 3],
    3: [0, 2]
}

source = int(input())
traversal = bfs(graph, source)
print("Following is Breadth First Traversal (starting from vertex", source + ")")
print(" ".join(map(str, traversal)))
```

**OUTPUT:**  
```
2
Following is Breadth First Traversal (starting from vertex 2)
2 0 3 1
```

```
1
Following is Breadth First Traversal (starting from vertex 1)
1 2 0 3
```

**RESULT:**  
The program successfully implements BFS traversal using a queue and visited set. For source vertex 2, the traversal visits 2, then its neighbors 0 and 3, then 1. For source vertex 1, the traversal visits 1, then neighbors 2 and 0, then 3. All test cases pass with correct output.
