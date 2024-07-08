Given a vertex u, return its set ID.

If vertices are stored in an array, we can find them in O(1). However this would result in [[Kruskal-Union(U, V)|Union(U,V)]] ending up with a time complexity of O(V) which is too slow.

Instead if we use a linked-list for storing the vertices, Kruskal's time complexity can be reduced to O(1).

However this changes the Find operation a little bit.

In a linked list: 
- Heads know their set ID.
- Traverse to the head to find the ID of an element in the list.
- This is O(size of the linked list).

Alternatively every node could hold information about its ID.
- Now find is O(1)
- But Union is slower because we have to update all IDs.

Instead we can use a **Linked Tree**

## Linked Tree

Suppose we have some linked nodes such as:
- 0->1
- 2->3
- 4
- 5

If we called union(1, 3) - connecting node 3 to 1.

Find would traverse parent pointers until finding a node whose parent is itself. This vertex ID is the set ID.

Union(U, V)
If find(U) != find(V) then we can set the parent(find(U)) = find(V).

In this case, Union(1,3) would connect node 2 (The parent of node 3) to node 0 (The parent of node 1).

## Time Complexity

- Union would be O([[Kruskal-Find(U)|Find]]).
- Find is in theory O(V) but if we can keep the heights of the tree low, then it will be at most O(max height).