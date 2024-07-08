Length of a path

Unweighted Graphs:
- The length of a path is the number of edges along the path.
Weighted Graphs:
- The length of a path is the sum of weights of the edges along the path.

Single Source, Single Target:
- Given a source vertex S and a target vertex T, return the shortest path from S to T.

Single source, all targets:
- Given a source vertex S, return the shortest paths to every other vertex in the graph.

There are several ways to tackle this:

- [[Breadth First Search]] (Single source, unweighted graphs)
- [[Dijkstra's Algorithm]] (Single source, weighted graphs with non-negative weights)
- [[Bellman-Ford Algorithm]] (Single source, weighted graphs including negative weights)
- [[Floyd-Warshall algorithm]] (All pairs, weighted graphs including negative weights)
