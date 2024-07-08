A way of encoding pairwise relations among a set of objects.

Each object is called a vertex or node.

Each connection is called an edge.

Maximum degree = Largest number of neighbours of a vertex/node in graph G.

Undirected graph : 
- A graph with connections (edges) between nodes (vertices) with no direction (Can go back and forth).

Directed Graph :
- A graph with edges between vertices with a direction (Cannot go backwards and forwards freely. Only in one specified direction).

Weighted Graph:
- A graph with edges that have an associated weighting (Or cost) attached to getting to another connected vertex. These graphs can be directed and with different weights attached to back and forth directions.
- To specify, two nodes can be connected back and forth like an undirected graph however they have a different associated weight (Going forwards might cost less than going backwards for example).

A graph can also be called a [[Tree]] under very specific constraints.

A graph is called sparse if E << V^2
- Where number of edges is significantly less than V^2

A graph is called dense if E is ~= V^2
- Where number of edges is close to the number of V^2

## Notation

Graph G = (V, E) where V is vertices and E is a set of edges.
Edge E = (u, v) where u and v are two vertices connected by the edge.

For undirected graphs, (u, v) = (v, u) because there is no direction.

For undirected graphs (u, v) =/= (v, u) because there is a direction.

A weighted graph is where each edge (u, v) has an associated weight w.

A graph is called a simple graph if it *does not have loops* and *does not contain multiple edges between same pair of vertices*.

### General concept for connected components

A vertex v is reachable from u if there is a path in the graph that starts in u and ends in v.

However there are some distinct differences between directed and undirected graphs:
- [[Directed Graphs]]
- [[Undirected Graphs]]

### Representing Graphs

There are two useful ways of representing a graph
- [[Adjacency Matrix]]
- [[Adjacency List]]

### Graph Traversal

Graph Traversal Algorithms traverse all nodes of a graph.

Two examples of algorithms that visit vertices exactly once:

- [[Breadth First Search]] (BFS)
- [[Depth First Search]] (DFS)

### Application of graph traversal

- Reachability
- Finding all connected components
- Testing a graph for bipartiteness (A graph is bipartite when we can divide it into two sets, U and V with every edge having one vertex in set U and the other in set V)
- [[Finding cycles]]
- [[Shortest Paths on unweighted graphs]]
- [[Topological sort]]
- [[Minimum Spanning Tree]]
- [[Shortest Path with Negative Weights]]
- [[All-pairs shortest paths]]
- [[Transitive Closure]]
- [[Network Flow]]

A unique form of a graph is the [[Bipartite Graph]] which can be useful for determining circulation with demands.