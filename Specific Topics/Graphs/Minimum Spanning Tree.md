The problem of finding the cheapest way to connect a set of nodes in a network. Arises in applications such as connecting cables in a network where several locations need to be connected together at a minimum possible cost.

[[Tree]]:
- A tree is a connected undirected graph with no cycles in it
Spanning Tree:
- A spanning tree of a general undirected weighted graph G is a tree that spans G (i.e a tree that includes every vertex of G) and is a subgraph of G (i.e every edge in the spanning tree belongs to G).
- The idea is basically decomposing the original graph G into a tree by removing repeated edges.

![[SpanningTree.png]]

- A spanning tree of a connected graph G is a maximal set of edges (Has the most amount of edges) that contains no cycles.
- It is also a minimal set of edges (Least amount of edges required) that connects all vertices.

## Minimal Spanning Tree (MST)

- Weight of a spanning tree is the sum of the weights of the edges in the tree.
- A minimum spanning tree of a weighted general graph G is a tree that spans G, whose weight is minimum over all possible spanning trees for this graph.
- There may be more than one minimum spanning tree for a graph G (e.g two or more spanning trees with the same minimum weight).
![[MinimumSpanningTreeWeights.png]]

## Constructing an MST

Let T denote the MST we are constructing, initialised as empty.
- An edge e is safe if {T Union e} is a subset of some MST.
##### General Strategy

- T = null
- While T can be grown safely:
	- find an edge e=<x, y> along which T is safe to grow
	- T = {T} union {<x, y>}
- return T

Some greedy algorithms we can use following this strategy to find a minimum spanning tree are:

- [[Prim's Algorithm]]
- [[Kruskal's Algorithm]]