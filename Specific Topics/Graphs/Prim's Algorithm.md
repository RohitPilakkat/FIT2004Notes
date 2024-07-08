Similar to [[Dijkstra's Algorithm]]. M is always a tree and, in each iteration, we choose the shortest edge connected to M avoiding cycles.

## Methodology

- Start by picking any vertex V to be the source of T
- While T does not contain all vertices in the graph:
	- Find the shortest edge e that goes from T to a difference connected component
	- add e to the tree T.

- Small modification of [[Dijkstra's Algorithm]].
	- We start with no edges in T, so there are V connected components in T (Each with a single node).
	- We select one node as the source.
	- At each iteration we add to T the shortest edge that links the connected component containing the source to a different connected component.
	- In each iteration, the number of connected components decreases by 1 and the number of nodes in the connected component containing the source increases by 1.
	- Cycles are avoided as no edges linking two nodes that are already in the same connected component are ever added to T.

### How does this differ from [[Dijkstra's Algorithm]]?

- Because the distance determined for each node is simply the shortest node from the current node checked, rather than checking the cumulative weight till that node. The relaxation process is dist\[v] > w(u,v) rather than dist\[v] > dist\[u] + w(u, v).

## Complexity Analysis

### Time Complexity

- Very similar to Dijkstra's Algorithm and its complexity is the same as Dijkstra's algorithm.
- O(V Log V + E Log V) if min-heap is used.
- Since the input graph G is connected, E >= V - 1. Hence the complexity can be simplified to O(E Log V) as E dominates V.

## Correctness

### Invariant Claim

Every iteration of Prim's algorithm the current set of selected edges in T is a subset of a minimum spanning tree of G.

### Base Case

The invariant is true initially when T is empty (No edges, therefore a subset of a minimum spanning tree. Or any tree for that matter)

### Inductive Step

- Assume T is a subset of some MST M at the start of some iteration. We must show that T is still a subset of some MST at the start of the next iteration.
	- i. e we want to show that after Prim's algorithm adds an edge, invariants still holds.
- Suppose the algorithm chooses a vertex E and an edge e = (C, E) to be the lightest edge that connects C in T to some E not in T (i.e this is the edge Prim's algorithm will choose in this iteration).
- If e is in T' (The MST graph) then T Union {e} is a subset of T', which is an MST, so the invariant holds.

### Contradiction Step

- Assume that T Union {e} is **NOT** a subset of an MST. 
- Let M be a minimum spanning tree that contains T' *but* excludes e=(C, E).
	- Vertex E must be connected to T in M (because M is a spanning tree). Since M does not contain e = (C, E) there must be a path that connects T with vertex E in M.
	- Let e = (C, B) be the first edge on the path that connects T to E.
- If we remove e = (C, B) from M and add e=(C, E) we will still get a spanning tree. Let this tree be called M'. 
- Since the weight of w(C, E) is smaller or equal to w(C, B) the weight of M' is smaller than or equal to M.
	- However this means M is not a minimum spanning tree, or that M' is also a viable minimum spanning tree.
- Therefore T, after adding e=(C, E), is a subset of a minimum spanning tree T.
	- i.e the invariant holds after adding edge e=(C, E).