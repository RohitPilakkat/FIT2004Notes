Given a graph G = (V, E), its transitive closure is another graph (V, E') that contains the same vertices V but contains an edge from node U to node V if there is a path from U to V in the original graph.

## Problem definition

What are the pairs of vertices (u, v) in the graph such that one can reach from u to v.
- e.g Given flights between different cities, can I go from city A to city B (disregarding the number of flights I need to take, I just want to get there).

## Solution

- Assign each edge a weight 1 and then apply [[Floyd-Warshall algorithm]].
- If dist\[i]\[j] is not infinity, this means there is a path from i to j in the original graph. 
- This shows us that there is a path that exists between our node. It does not matter what the path to it is.

## Complexity Analysis

### Time Complexity
- O(V^3)

### Space Complexity
- O(V^2)