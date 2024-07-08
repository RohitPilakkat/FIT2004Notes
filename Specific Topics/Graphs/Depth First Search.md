Traverses the graph as deeply as possible before backtracking and traversing other nodes.

This **MUST** reach the end of the traversal otherwise it cannot be considered a depth first search as it has not reached the deepest point possible (Or has traversed all vertices in that branch yet).

Uses a stack (LIFO).

### Time Complexity

- Each vertex visited at most once
- Each edge accessed at most twice (Once when U is visited, once when V is visited)
- Total Cost:- O(V+E)

### Space Complexity

- O(V+E) assuming an adjacency list

## DFS Cycle Finding

DFS can be used to find cycles in an undirected graph.

If at any point the search finds an edge that leads to a vertex that has already been visited then this edge connects two vertices that are already connected and hence forms part of a cycle.
### DFS Shortest Path (Topological Sort)

This gives us one possible topological sort by checking the deepest the algorithm can reach by following a path and then checking the next deepest to see what the relation is between these paths.

When a node has been visited and is the current deepest node, it will get pushed to a heap or stack.