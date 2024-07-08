In directed graphs, reachability is :

- Reflexive: Each u node is reachable from itself
- Transitive: If v is reachable from u, and u is reachable from w, then v is reachable from w 
- Not guaranteed to be symmetric.

Vertices u and v are called mutually reachable if there are paths from u to v and from v to u.

Recall that (u, v) is not necessarily (v, u) in a directed graph.

Mutual reachability is an equivalence relation and decomposes the graph into strongly-connected components (For any two vertices u and v, their strong components are either identical or disjoint).

What this means is that in a directed graph, if you can reach node A from node B and then reach node B from node A, these are strongly connected components.

A directed graph, as a whole, is strongly connected if for every pair of vertices u and v of G there are paths from u to v and from v to u.

This would imply the graph has one strongly-connected component.