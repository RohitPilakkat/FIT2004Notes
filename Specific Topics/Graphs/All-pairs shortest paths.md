## Problem Definition

Return shortest distances between all pairs of vertices in a connected graph

1. For unweighted graphs:
	- For each vertex V in the graph
		- Call [[Breadth First Search]] for V
	- Time Complexity:
		- O(V(V+E)) = O(V^2 + EV) -> O(EV) for connected graphs where O(V) <= O(E).
		- For dense graphs, E is O(V^2) therefore total cost is O(V^3) for dense graphs.

2. For weighted graphs with non-negative weights:
	- For each vertex V in the graph
		- Call [[Dijkstra's algorithm]] for V
	- Time Complexity:
		- O(V(E Log V)) = O(EV Log V))
		- For dense graphs: O(V^3 log V)

3. For weighted graphs with negative weights
	- For each vertex V in the graph
		- Call [[Bellman-Ford Algorithm]] for V
	- Time Complexity
		- O(V(VE)) = O(V^2 E)
		- For dense graphs: O(V^4)

These are very high values if we're finding shortest distances for all pairs.
What we can do instead is use:

[[Floyd-Warshall algorithm]] 

which can do this in O(V^3) even with negative weights.
