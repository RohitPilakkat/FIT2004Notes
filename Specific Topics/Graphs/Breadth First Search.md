Traverses the graph uniformly from the source vertex.

All vertices that are k edges away from the source vertex are visited before all vertices that are k+1 edges away from source.

This algorithm will attempt to check the first layer away from the source before moving onto the next layer.

Uses a queue (FIFO).

### Time Complexity

- Each vertex is added to the queue (FIFO) at most once
	- We insert vertices to the queue at most O(V) times
- Each edge accessed at most twice (Once when u is visited, once when v is visited)
- Visited is just a bit list of length V indexed by the vertex ID
	- Lookup and update are both O(1) since it can be indexed
- O(V+E)
	- Every vertex must be added to the queue and then every edge is accessed atleast once, max twice.

### Space Complexity

- O(V+E)
	- This is because we have an input size of O(V+E) from the adjacency list.


#### Note

For each edge that connects the vertex we have taken from the queue, if the vertex we are visiting (v) has not already been visited, then set its visited parameter to true and add it to the queue. Otherwise, ignore because already visited.
## BFS Shortest Path

- Initialise an array Distance with infinity as values for each vertex.
- Add source vertex A to the Queue and set its distance to 0
- While the Queue is not empty
	- Get the first vertex V from the queue
	- For each adjacent edge (v, u)
		- If U' distance is infinity
			- Insert U at the end of the queue
			- distance\[U] = distance\[V] + 1

- Distances are stored in an O(1) lookup structure
- Distances are set by lookup at the distance of the current vertex and adding 1
- Path from S to V can be found by backtracking from V to S using the array pred.
- Array pred is just an array that holds the predecessor vertex when moving onto the next vertex (That is directly connected to the currentt vertex).
- Complexity is same as regular BFS O(V+E).