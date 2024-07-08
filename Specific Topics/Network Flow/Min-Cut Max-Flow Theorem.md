A cut of a flow network partitions the vertices of the network into two disjoint partitions S and T such that source S is in S and target T is in T.
- eg:- S = {s, a, b} and T = {t, c, d}

The cut-set of a cut (S, T) is the set of edges that cross the cut i.e
- each edge connects one vertex in S with another in T.
	- The edges that have direction from a vertex in S to a vertex in T are called outgoing edges of the cut.
	- The edges that have direction from a vertex in T to a vertex in S are called incoming edges of the cut.


Capacity of a cut (S, T) is just the total capacity of its outgoing edges.

Flow of a cut (S, T) is total flow of outgoing edges - total flow of incoming edges.

Flow of a cut is always less than or equal to the capacity of the cut.

Basically, by cutting the graph into two partitions where we separate the source and sink nodes into two distinct, disjointed graphs we can determine what the max flow is by seeing what the edges add upto (By determining what the total flow is considering the outgoing and incoming flow).