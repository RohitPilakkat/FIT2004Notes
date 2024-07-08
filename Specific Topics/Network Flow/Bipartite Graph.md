A graph where the vertices can be separated into two disjoint subsets L and R such that every edge connects a vertex U in L to a vertex V in R.

## Maximum Bipartite Matching

Given a bipartite graph G=(V, E) with V=LUR, a matching is a subset M of edges E such that no vertex v belonging to V is incident to multiple edges in M. The maximum bipartite matching problem seeks a matching of the graph with the largest possible number of edges.

If the number of vertices in L and R are the same and the matching has exactly the same number of edges as vertices then it is called a perfect matching (There is exactly one edge for each matching).

This maximum matching problem can be identified using [[Network Flow]] theory.

A corresponding flow network can be constructed where the key idea is to use units of flow to represent matches.
- Add a source node and connect all the nodes in L
- Add a sink node and connect all nodes in R to it.
- Direct all original edges to point from L to R.
- Give each edge a capacity of 1.![[bipartiteNetworkFLow.png]]

Since every edge has a capacity of 1, at most one unit of flow can be sent from s through any vertex u belonging to vertex in L.

This ensures that, when using [[Ford Fulkerson Algorithm]], each node in L has at most one outgoing edge and each node in R has at most one incoming edge.