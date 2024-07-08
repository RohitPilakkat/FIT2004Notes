The empty tree is a BST (Binary Search Tree)

If the tree is no empty
- The elements in the left subtree are less than the element at its root
- The elements in the right subtree are greater than the element at its root
- The left subtree is a BST
- The right subtree is a BST

This structure **must** be maintained throughout the tree when looking at each individually smaller subtree.


## Complexity Analysis

### Worst Case

- A BST is not a balanced tree and, in worst case, may generate to a linked list
- Time Complexity in this case
	- Insert: O(N)
	- Delete: O(N)
	- Search: O(N)
How do we improve upon this worst case scenario? We can keep the tree balanced regardless of what order elements are inserted into the tree.

We can implement [[AVL (Adelson-Velskii Landis tree)]].