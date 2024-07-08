The power of [[Network Flow]] algorithms like [[Ford Fulkerson Algorithm]] is that they allow us to efficiently solve non-trivial combinatorial problems that in principle have nothing to do with flow of material or data in a network.

- Solving the maximum [[Bipartite Graph]] matching problem was a simple example.
There are many examples that are possible and we have a useful generalisation to solve these kinds of problems. These problems can be reduced into a standard max-flow problem and therefore solved using [[Ford Fulkerson Algorithm]].

In a problem of Circulation with Demands there is no single source or sink.

Every node can have both an incoming and outgoing edge.

Each node U has an associated number d<sub>u</sub> that denotes its condition

![[CirculationWithDemandGeneral.png]]

<sup>Note that this graph has a minor mistake. d<sub>y</sub> and d<sub>x</sub> should be d<sub>u</sub> less than zero </sup>

If d<sub>u</sub> > 0 then node u has a demand of d<sub>u</sub> units of flow.
- It wants to receive in its incoming edges d<sub>u</sub> units of flow more than what it sends out in its outgoing edges.

If d<sub>u</sub> < 0 then node u has a supply of -d<sub>u</sub> units of flow
- It wants to receive in its incoming edges d<sub>u</sub> units of flow less than what it sends out in its outgoing edges.

If d<sub>u</sub> = 0 then node u wants to keep the balance between the incoming and outgoing flow in its edges 
- Similar to all non-sink and non-source nodes in the standard max-flow problem.

The Circulation with Demands problem is to determine the feasibility of satisfying these constraints together with the capacity constraints.

- A necessary condition for obtaining a feasible solution is that the sum of demands in the network should be 0, but this is not a sufficient condition to get a correct solution.

## Formal Definition of Circulation with Demands Problem

### Property 1: Capacity Constraint

- For each edge (u, v) its flow denoted as f(u,v) is bounded by its capacity
	- 0<= f(u,v) <= c(u,v) where c(u,v) is the capacity of the edge.
	- We consider integer capacities and demands.

### Property 2: Demand Constraint
- For any node u, it should hold that 
	- Sum of back flows f(v, u) - Sum of forward flow f(u, v) = d<sub>u</sub>

To solve this efficiently, we must be able to reduce the circulation with demands problem to a standard max-flow problem so that we can use [[Ford Fulkerson Algorithm]] to solve it.

The idea is to create a super graph G' of G, solve a max-flow problem in G' getting a solution f', and translate f' to a solution for the circulation with demands problem in G.

## Methodology

1. Add each node and edge of G in G'![[CirculationWithDemandsStep1.png]]

2. Add a super-source node s. ![[CirculationWithDemandsStep2.png]]

3. For each node u of G with d<sub>u</sub> < 0, add an edge (s, u) to G' with capacity - d<sub>u</sub>.![[CirculationWithDemandsStep3.png]]

4. Add a super-sink node t.![[CirculationWithDemandsStep4.png]]

5. For each node u of G such that d<sub>u</sub> > 0 add an edge (u,t) to  G' with capacity d<sub>u</sub>.![[CirculationWithDemandsStep5.png]]

6. Solve the max flow problem in G' using [[Ford Fulkerson Algorithm]].


The circulation with demands in G has a feasible solution if and only if
- The solution of the max-flow problem in G' saturates all the outgoing edges of S and all the incoming edges of T.
- This relates to the necessary condition of 
	- Sum of d<sub>u</sub> = 0.
- If that is the case, a feasible solution can be found by just deleting the additional nodes and edges of G'.

## Edges with Lower Bounds

When considering edges with lower bounds.
This is an enforcement that atleast a specified amount of flow goes through the edge.

To solve this what we can do reduce it to a circulation with demands (with no lower bounds) and follow the same steps we do with solving a circulation with demands problem above.

We do this by 
- first breaking down the solution into a fixed flow that satisfies the lower bounds.
- Breaking it down into a circulation with demands problem without lower bounds on a graph with adjusted capacities and demands to account for the fixed flow. The demand is reduced based on the incoming and outgoing flow from the lower bound demands.
- Essentially we are just doing creating one graph with solutions pertaining to the exact amount required for the lower bounds and then creating another graph for solutions pertaining to the leftover capacity that we need to fill.

The original problem has a feasible solution if, and only if, the adjusted circulation problem (without lower bounds) has a feasible solution.

In that case, the original problem solution can be obtained by just summing the fixed flow to the solution of the adjusted problem.