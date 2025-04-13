# Search Algorithms
So first of all what is AI 
It is the study of how to make computers do things at which at the moment humans are better.
It is the study of building agents that acts rationally.


>[!gemini]+ Gemini
>## Difference between Uninformed and Informed Search
> 
> ### Uninformed Search
> 
> - **Definition:** No information about the goal is given.
> - **Exploration Strategy:** Trial-and-error or random exploration.
> - **Example Algorithms:** Depth-First Search (DFS), Breath-First Search (BFS), Uniform Cost Search
> 
> ### Informed Search
> 
> - **Definition:** Uses information about the goal to guide the search.
> - **Heuristic Function (h(n)):** Estimates the distance from the current node to the goal.
> - **Exploration Strategy:** Prioritizes nodes with lower h(n) values.
> - **Example Algorithms:**
>     - Best-First Search (BFS)
>     - A* Search
>     - Greedy Search
 

![[Pasted image 20250212162656.png]]

# Small notes on Branching factor
![[Pasted image 20250212163847.png]]
![[Pasted image 20250212163939.png]]

# Now Uninformed Search
## So we have BFS, DFS and Uniform Search
# BFS


>[!gemini]+ Gemini
>## Breadth-First Search (BFS) in AI 🌳
> 
> ### Definition
> 
> BFS is a graph traversal algorithm that explores the neighbors of a node before moving on to the next level. It maintains a queue to keep track of the nodes to be explored.
> 
> ### Pseudocode
> 
> ```python
> def BFS(graph, start):
>     queue = [start]
>     visited = set()
> 
>     while queue:
>         node = queue.pop(0)
>         if node not in visited:
>             visited.add(node)
>             for neighbor in graph[node]:
>                 if neighbor not in visited:
>                     queue.append(neighbor)
> ```
> 
> ### Algorithm
> 
> 1. Initialize a queue with the starting node.
> 2. While the queue is not empty:
>    - Pop the first node from the queue.
>    - Mark the node as visited.
>    - Add all unvisited neighbors of the node to the queue.
> 
> ### Applications
> 
> - Finding the shortest path between two nodes in a graph.
> - Maze solving.
> - Network traversal.
 
![[Pasted image 20250212164430.png]]![[Pasted image 20250212164611.png]]

# DFS
![[Pasted image 20250212170117.png]]
![[Pasted image 20250212170609.png]]
# Iterative Deepening
![[Pasted image 20250212172014.png]]
# Uniform Cost Search is also called **Dijkstra's Algorithm**.
![[Pasted image 20250212173708.png]]


# Informed Search
# Heuristics Search Algorithm

