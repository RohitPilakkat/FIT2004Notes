Given two vertices u and v, if they have different set IDs, union the two sets they belong to (and update all the set IDs of the vertices in one of the sets).

If vertices are stored in an array unfortunately time complexity of this function would be O(V) in worst case which is not good enough.

Linked Lists can instead be used to union as we can just append one linked list to another in O(1) operation.

However this does change the [[Kruskal-Find(U)|Find(U)]] function time complexity as to find the set ID of the node we would need to traverse the entirety of the linked list to check the ID of the head. This takes O(Linked List Size)

An option to improve Find(U) is to let all linked list nodes know what their ID is.

This improves Find(U) to O(1) however now Union(U, V) must update the IDs of all Linked List nodes to the new ID which can take time.

Instead we can use a **linked tree**

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