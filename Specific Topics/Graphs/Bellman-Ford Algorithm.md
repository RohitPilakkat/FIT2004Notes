## Core Idea

If no negative cycles are reachable from node S, then for every node T that is reachable from S there is a shortest path from S to T that is simple (i.e, no nodes are repeated).
- Cycles with positive weight cannot be part of a shortest path
- Given a shortest path that contains cycles of weight 0, the cycles can be removed to obtain an alternative shortest path that is simple.

What is the maximum number of edges in a shortest path between two vertices ignoring zero-weight cycles and assuming there is no negative cycles in the graph?

- V-1 maximum number of edges, because a shortest path is essentially just a [[Tree]].
- So the number of iterations we would need is V-1
- Any simple path has at most V-1 edges.

This is essentially a form of [[Dynamic Programming]]. 

We use notation such as OPT(3, x) where this defines an optimal shortest distance from our source node to x while considering only paths with at most 3 edges.

We can build this up slowly (Or recursively find this and memoise) to find our true optimal solution using a dynamic programming approach.

### Example

Assume we know OPT(3, b) for every vertex B in the graph.
If we want to compute OPT(4, b) then we must check two cases.

- Case 1: 
	- OPT(4, b) = OPT(3, b)
- Case 2:
	- OPT(4, b) = OPT(3, a) + w(a,b).
	- Here we are considering every edge (a->b) and picking the smallest possible edge.
From these two cases we must then find which is the minimum between the two. This is the exact same approach that a lot of dynamic programming solutions use.

### Formal Definition

For a source node S, let OP(i, V) denote the minimum weight of a S->V path with at most i edges.

Let P be an optimal path with at most i edges that achieves total weight OPT(i, V).
- If P has at most i-1 edges, then OPT(i, V) = OPT(i-1, V).
- If P has exactly i edges and (u, v) is the last edge of P, then OPT(i, V) = OPT(i-1, u) + w(u, v), where w(u, v) denotes the weight of edge (u, v).

![[bellmanFordRecursive.png]]

## Complexity Analysis

### Time Complexity

O(VE)
- To compute M\[i, v] you will need to check all incoming edges of vertex which is why the inner for loop executes O(E) times.

### Space Complexity

O(VE)
- Like most dynamic programming solutions we need a matrix table that holds the solutions for every vertex and every possible edge that you can add onto it.

## Methodology run through

### First Iteration
- For each vertex B in the graph
	- For each edge(a,b) in the graph
		- Dist\[b] = min(Dist\[b], Dist\[a] + w(a, b))
What we're doing here is looking at each vertex, and looking at each of its incoming edges. We are only considering paths of size 1.
We then find an optimal solution for each node that goes to our target node based on the minimum distance to get there.

### Second Iteration
- We move onto paths of size 2.
- Because all our vertices have been relaxed using paths of 1, we can assume that if there exists an optimal solution to get to that node, they are paths of either size 1 or size 2.
- For each vertex B in the graph, we again try
	- For each edge(a, b) in the graph
		- Dist\[b] = min(Dist\[b], Dist\[a] + w(a, b))

### Early stopping

- We can implement an early stop condition if nothing changes in an iteration. If we notice that nothing has changed within an iteration, bellman-ford algorithm can be stopped early and we can output the current values.

### Negative Cycles

- If dist\[b] for any vertex b decreases after the V-th iteration this implies
	- That there is a negative cycle in the graph (Because the path consists of V or more edges)
	- We run V-th iteration to see if there are negative cycles
	- If V-th iteration reduces the distance of a vertex, this means that there is a shorter path with at least V edges which implies that there is a negative cycle.
- Bellman-Ford algo will only find negative cycles if a cycle is reachable from the source vertex.

To detect a negative cycle reliably, we can add one extra super source node that has an edge from it to every other node and then run Bellman-Ford on the added node. The weights of these edges would be 0 in order to prevent the weightings from influencing the results.

## Some assumptions we can make

- There is a guarantee that after i iterations dist\[v] <= OPT(i, v) for every V in the graph.
	- Dist\[v] is the distance from S to V computed by the algorithm after i iterations.
	- OPT(i, v) is the total weight of the shortest path from S to V that uses at most i edges.
- Note that we cannot say dist\[v] = OPT(i,v) for every vertex V in the graph. This is because dist\[v] could be smaller than OPT(i, v) depending on the order in which edges are relaxed.

### Modifying Bellman-Ford to determine which vertices have valid distances, and which are affected by the negative cycle

- Since we know that V-1 iterations are performed for each node, we can just run V additional iterations to see if there are nodes whose values keep changing. If it does, we set them to -infinity because we know they are invalid distances.