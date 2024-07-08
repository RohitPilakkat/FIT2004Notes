### Undirected Graph

Create an array of size V.
At each V\[i] store the list of vertices adjacent to the ith vertex.

![[AdjacencyListUndirectedGraph.png]]

### Undirected Weighted Graph

Create an array of size V. At each V\[i], store the list of vertices adjacent to the ith vertex along with the weights.

![[AdjacencyListUndirectedWeightedGraph.png]]

### Directed Weighted Graph

Create an array of size V. at each V\[i] store the list of vertices adjacent to the ith vertex along with the weights.

![[AdjacencyListDirectedWeightedGraph.png]]

## Complexity Analysis

### Space Complexity

O(V+E) as you're storing all the nodes and then all the edges that are connected to it (Technically this would be O(V+2E) for each node that is duplicated between connected nodes however this decomposes into O(V+E))

### Time Complexity of checking if a particular edge exists

O(log V) assuming each adjacency list is a sorted array on vertex IDs. This is because we want to check if an edge connects node V to node U, we can call node V in O(1) time but we must check through the entire list of edges for that node to see if it is connected to node U.

### Time complexity of retrieving all adjacency vertices of a given vertex.

O(X) where X is the number of adjacent vertices.