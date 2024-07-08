## Intuition

We start off with a flow network where we haven't yet reached our maximum flow. We can then determine a way to make space within a potential edge that can allow us the capacity to send a little more flow to achieve our true maximum flow.

## Residual Network

- Residual network has the same vertices as the original network
- For every directed edge u->v in flow network, we add two edges in the residual network:
	- Forward Edge/Residual Edge: 
		- An edge in the same direction as u->v with the residual/remaining capacity.
	- Backward edge/Reversible flow edge:
		- An edge in the direction opposite to u->v (i.e v->u) with weight equal to the current flow of u->v in the flow network![[ResidualNetwork.png]]

## Augmenting Path

Augmenting path is any simple path (A path without repeating vertices) from source s to target t.

- Residual capacity of a path is the minimum edge weight of this path. This is the smallest weighted edge left on the path in the residual network.
- For each edge along this path we can push additional flow equal to the residual capacity of the path in the flow network.![[augmentedflownetwork.png]]

## Complexity Analysis
- Cost of finding an augmenting path
	- Using BFS, cost is O(V+E) (Or just O(E) since the graph is connected. There are usually more or equal edges to the number of vertices).
- Augmenting flow along a path
	- length of path <= V, so cost is O(V).
- Updating the residual
	- Same amount of work as updating flows along the augmenting path O(V)
Therefore total work in one iteration of a loop is
- O(V+E) = O(E) since E is usually the dominating factor in a connected graph.

- Each iteration of Ford Fulkerson flow grows by atleast 1.
- If maximum flow in graph is F
- Maximum number of iterations is also F (Worst-case is when flow is increased by 1 every iteration).

Therefore total work = O(EF).
- It is actually O(VE^2) when using BFS to find augmenting paths.

## Proof of correctness
- Does the algorithm terminate?
	- Yes because the flow always increases by atleast 1 per iteration and there cannot be any augmenting paths if all source's outgoing edges are saturated.
- In order to show that the algorithm terminates exactly once it finds a flow whose value is the maximum possible value among all feasible flows, we can use the [[Min-Cut Max-Flow Theorem]].