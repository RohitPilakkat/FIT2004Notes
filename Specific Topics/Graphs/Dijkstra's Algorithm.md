Algorithm for solving the single source, all targets, shortest path problem on graphs with non-negative weights. Very similar to [[Breadth First Search|BFS]] but allows us to find shortest path when considering weight (In a positive weighted graph).

- Keeps track of a set of S nodes whose distance to the source has already been determined (Invariant. at i = 0 this is 1, the source node).
- Initially S only contains the source node, and it grows by one element at a time until containing all nodes that are reachable from the source node.
- At each iteration, from all nodes that are one edge away from S, add to S the node u that has the smallest distance to the source.

## Methodology

- A priority queue is maintained (Min Heap priority queue where priority is distance)
- Two ID-indexed arrays are maintained (Pred and Distance)
![[DijkstraGraph.png]]

- For each neighbour of V of U, relax along that edge if
	- If dist\[u] + w(u, v) < dist\[v]
- In plainer terms, from our current node we will check all possible paths to the neighbours are and note down what the distance is from our current node. Our priority queue, since it is queued up based on smallest distance, will check the next closest node and check its distance to its neighbours.
- If it so happens that there exists a neighbour with an already calculated distance that is higher than the total distance from our source to our current neighbour and then to the neighbour, we will consider this a shorter path and set the distance of this neighbour as the new distance and set its predecessor as the current node.

## Complexity Analysis

### Time Complexity

- While loop executes O(V) times (The priority min heap queue holds all possible vertices)
	- Find the vertex with the smallest distance and delete it. (Generally time of O(Log V))
- Each edge visited once -> O(E)
	- Updating the priority queue: depends on implementation (Generally O(Log V))
- Total Cost = O(E\*Log N + V\*Log V)
- If the graph is connected, minimum value of E is V-1. It could be more however so generally E dominates V.
- Total Cost is then: O(ELogV).

## Proof of Correctness

## Claim

For every vertex V which has been removed from the queue (i.e finalised), dist\[v] is correct (i.e dist\[v] is the shortest distance from S to V)

### Base Case

dist\[S] is initialised to 0, which is the shortest distance from S to S (since there are no negative weights).

## Inductive Step

- Assume that the claim holds for all vertices which have been removed from the queue (S)
- Let U be the next vertex which is removed from the queue (to be finalised in this iteration).
- Assume that dist\[U] is **NOT** the shortest distance from S to U (Proof by contradiction).
- This implies there exists a path P from S to U that is shorter than dist\[U] (e.g P is S->X->Y->U).
- If this is the case, then path P must contain atleast one vertex other than U that is not finalised. 
- Our assumption made however is that the vertices popped from the queue are finalised, which contradicts the fact that the smallest distance amongst the finalised vertices contains a vertex that has not been finalised.
