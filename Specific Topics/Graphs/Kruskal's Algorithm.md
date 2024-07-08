Process edges in ascending order of edge weights and M is a forest (i.e a set of [[Tree|trees]]).

## Methodology

- We start with no edges in T, so there are V connected components in T ( each with a single node).
- We process edges in ascending order of edge weights, and add an edge e to T if this addition does not create a cycle.
- Each time that one edge E is added to T, E is the smallest edge that links two distinct connected components of T.
- Cycles are avoided as no edges linking two nodes that are already in the same connected component are ever added to T.
- At any point of the execution T is a forest (i.e a set of trees).

### Detailed Steps

- Kruskals(G(V, E))
	- Sort the edges in ascending order of weights.
	- Let T be a graph with V as its vertices, and no edges.
	- For each edge (v, u) in ascending order
		- If adding (v, u) does not a create a cycle in T
			- Add(v, u) to T
	- Return T
- Each time that one edge E is added to T, E is the smallest edge that links two distinct connected components of T.
- Intuitively Kruskal's algorithm runs for V-1 Iterations and in each iteration it merges the two distinct connected components that have the smallest distance between themselves (As the edges are sorted by weight).

#### Determining if an edge will create a cycle

- An edge can be added if it does not create a cycle
- An edge can be added if it is not between two nodes which belong to the same connected component. (eg. A->B  cannot be added if A->C->B exists in the tree as a lower weight edge).
- Adding an edge between two distinct/disjoint connected components merges those connected components into one. (Therefore a cycle can't happen, since they are disjointed components).

## Finding the set of a vertex, and the union of two sets

We can define two operations [[Kruskal-Find(U)|find(u)]] and [[Kruskal-Union(U, V)|union(u,v)]] to help us with this. These algorithms *must* be fast to make this method viable. If we just store vertices in an array, Find would be O(1) however union would be O(V).

With a linked tree instead, we have:
- Union = O(Find)
- Find = O(max_height)

However this is not as fast we want as we assumed the cost of UNION_SETS to be O(V) for each call leading to overall cost of O(EV) as we are calling a union for each edge that we check.

When checked closer however with the right assumptions, UNION_SETS is O(V Log V). Analysis below.

## Complexity Analysis

### Time Complexity

#### Sorting Edges: O(E Log E)

- E Log E < = E Log V^2 (As we assume E <= V^2 for a sparse graph)
- 2E Log(V) -> O(E Log V).
#### Initialisation of Union Find

- O(V)
#### For Loop Execution

- Executes O(E) times
	- SET_ID() takes O(x) where x is the height of the tree
	- UNION_SET() takes O(1) + 2 finds, so it takes O(X) where x is the height of the deeper of the two trees to be unioned (Which is at most V).

- We can show that, when using the union-by-size rule the number of elements N in any tree is atleast 2^h where h is the height of the tree.
- Therefore, h <= log2(N).

- Union takes 2 finds + O(1) effort.
- Find takes effort equal to the height of the tree, which is <= log2N.
- So union is O(log2N), where N is the number of nodes of the taller tree being unioned.

- How many unions in total do we need to perform?
	- We perform V-1 Unions.

- Each one has a worst case cost of O(Log V) (This is an over-estimation).
- So the total cost of all unions is bounded by O(V Log V).

Therefore, total cost now becomes:

- O(E Log V + V Log V) -> O(E log V).


## Correctness

### Invariant Claim

- Every iteration of Kruskal's algorithm, the current set of selected edges in T is a subset of some minimum spanning tree of G.

### Base Case

- The invariant is true initially when T is empty.

### Inductive Step

- Assume that T is currently a subset of some MST. We show that after Kruskal's adds an edge, it is still a subset of an MST.
- At an arbitrary step the algorithm combines two sets (Assume S1, S2) using an edge E with weight w.
### Contradiction step

- Assume that {T U E} is **not** a subset of any MST.
- Let M be a minimum spanning tree that contains T but excludes the edge E we have selected.
- There must be a path between our vertices in M
- Let E2 be an edge that is **NOT** in T and is on a path between two vertices in each of the sets of our original two vertices.
- We will get a spanning tree if we add the original edge into M and remove our new edge. This new tree can be referred to as M'.
- Since the weight of M' is smaller or equal to M because the old weight is smaller or equal to the new weight, M' is actually a minimum spanning tree therefore the invariant holds true after adding this edge into T.
