In an undirected graph, reachability is an equivalence relation. 
This means: 
- Each u node is reachable from itself.
- If v is reachable from u, then u is reachable from v.
- if v is reachable from u, and u is reachable from y then v is reachable from y.

The set of vertices reachable from u defines the connected component of G containing u.

An undirected graph is connected if all vertices are part of a single connected component.

If for any pair of vertices u and v, there is a path between them in graph G then we can say this graph is connected.

A graph that is disjointed is one where there is no feasible path (A collection of edges) that can connect any vertex u with any vertex v.

Let G be a graph.

The minimum number of edges in a connected undirected graph in terms of V:
- V-1 = O(V)
- This means, the minimum number of edges required for a graph with V nodes is V-1 (An edge connecting each node).

The maximum number of edges in an undirected graph in terms of V:
- V(V-1)/2 = O(V^2)
- Every node is connected to every other node. Since each edge connecting a node to another node is also an edge connecting the other node to the current node, we can divide it by 2 (Repeated edge not considered).

A graph is called sparse if E << V^2
- Where number of edges is significantly less than V^2

A graph is called dense if E is ~= V^2
- Where number of edges is close to the number of V^2

