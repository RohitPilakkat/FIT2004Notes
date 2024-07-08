A subset of [[Graphs]], specifically connected [[Directed Graphs]].

A flow network is a connected directed graph where:
- There is a single source vertex and a single sink/target vertex
- Each edge has a given (non-negative) capacity (usually an integer).

Flow networks typically model real world problems like:
- Water flowing through pipes
- electrical current flowing through electrical circuits
- Information flowing through communication networks.

They can also be used to solve a large range of other combinatorial problems unrelated to physical flow

## Basic Notation

Set of all incoming edges to a vertex V: E<sub>in</sub>(V)
- E<sub>in</sub>(b) = s -> b, c->b
- E<sub>in</sub>(a) = ?
Set of all outgoing edges from a vertex V: denoted as E<sub>out</sub>(v)
- E<sub>out</sub>(b) = b -> d
- E<sub>out</sub>(a) = ?

Source Vertex: denoted as S (has no incoming edges)
Sink/Target vertex: denoted as T (has no outgoing edges)

## Flow

Flow is an assignment of how much material is flowing through each edge in the flow network given its stated edge capacity.![[FlowDiagram.png]]

- All vertices (except S and T) conserve their flow. 
	- The total amount flowing into any vertex (through incoming edges) is
	- =
	- The total amount flowing out of that vertex (through outgoing edges)
- This is a property called flow conservation

## Properties of a Flow Network

### Property 1 - Capacity Constraint
- For each edge e, its flow denoted as f(e), is bounded by the capacity of its edge, i.e, 0 <= f(e) <= c(e) where c(e) is the capacity of the edge.

### Property 2 - Flow Conservation
- For any vertex v (except S and T) the total flow coming into the vertex must be equal to the total flow going out from this vertex - FORMAL DEFINITION

A common problem that we want to solve with Flow Networks is the:

[[Maximum Flow Problem]]

Another common problem we might want to solve is

[[Circulation with Demands and Applications of Network Flow]]