### Undirected Graph
Create a V x V matrix M and store T (True) for M\[i]\[j] if there exists an edge between ith and jth vertex. Otherwise, store F (False).

Can use 1s and 0s instead.

![[AdjacencyMatrix.png]]

### Undirected Weighted Graph

Create a V x V matrix M and store weight at M\[i]\[j] only if there exists an edge between ith and jth vertex.

![[AdjacencyMatrixWeightedUndirected.png]]

### Directed Weighted Graph

Create a VxV matrix M and store weight at M\[i]\[j] only if there exists an edge from ith to jth vertex.

![[AdjacencyMatrixWeightedDirected.png]]


## Complexity Analysis

### Space Complexity

O(V^2) regardless of number of edges because you *have* to make a V x V matrix.

### Time Complexity of checking if an edge exists

O(1) because you can instantly index it

### Time Complexity of retrieving all neighbours of a given vertex

O(V) regardless of number of neighbours as you must check all spots of a chosen node (Need to check all other Vertices to check if there is a connection).