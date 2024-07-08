An algorithm based on dynamic programming.

If the graph has a negative cycle, it will always be detected.

This is distinct from [[Bellman-Ford Algorithm]] because Bellman Ford only detects negative cycles that are reachable from the source node.

A shortcut path is found between node i and node j if there is an intermediate vertex K that creates a shorter path than the current path between i and j.
## Methodology

- Initialise an [[Adjacency Matrix]] called Dist\[]\[] considering adjacent edges only
- For each vertex K in the graph
	- For each vertex i in the graph
		- for each vertex j in the graph
			- if dist\[i]\[j] > dist\[i]\[k] + dist\[k]\[j]
			- as in if dist(i->k->j) is smaller than the current dist (i->j)
				- update dist\[i]\[j] = dist\[i]\[k] + dist\[k]\[j]
				- create a shortcut i->j with weight equal to dist i->k->j

### Complexity Analysis

#### Time Complexity:
- As we have to do 3 loops, a loop for each node and for each variation of intermediate node, we need 3 loops.
	- O(V^3)

#### Space Complexity:
- As we have to store an adjacency matrix to keep track of the distances:
	- O(V^2)

## Proving correctness

Invariant: Distance\[i]\[j] corresponds to the shortest path from i to j considering only intermediate vertices 1 to k-1.

#### Base Case
k = 1
- True because dist\[]\[] is initialised based only on the adjacent edges

#### Inductive Step (example k =4)
- Assume dist\[i]\[j] is the shortest path from i to j considering only vertices 1 to k-1
- if k-th vertex is to improve on the known path from i to j, it can only be by going from i to k and then k to j (possibly via vertices in 1 to k-1)
	- Thus minimum of dist\[i->k->j] and dist\[i->j] gives the minimum distance from i to j considering the intermediate vertices 1 to k.

## Negative Cycles

- If there is a negative cycle, there will be a vertex V such that dist\[v]\[v] is negative
- Look at the diagonal of the final resultant matrix and return error if there is a negative value found.
- If there is no negative cycle, the distance from the node to itself *should* be 0 however if there was a negative cycle it will find a path the leads to a negative value that improves upon this distance but gets stuck in this cycle.