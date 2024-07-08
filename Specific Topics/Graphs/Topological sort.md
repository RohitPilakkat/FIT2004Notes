Usually done on [[Directed Acyclic Graphs (DAG)]].

Order of vertices in a DAG:
- A < B if A -> B
- Note that if A->B and B->D, we have A < B and B < D which implies A < D (transitivity).

Some vertices may be incomparable:
- A vertex that lays on the same layer as another vertex maybe be incomparable. For example, if we can say A < B and A < C we can't necessarily say A < C

A topological order:
- Is a permutation of the vertices in the original DAG such that
- for every directed edge u->v of the DAG
	- u appears before v in the permutation
- A DAG can have many valid topological sorts. E.G let u and v be two incomparable vertices. U may appear before or after V in a topological sort.

Topological sort can be done using Kahn's Algorithm (Not assessed in this unit).

We can also use [[Depth First Search|DFS]] instead for topological sorts.