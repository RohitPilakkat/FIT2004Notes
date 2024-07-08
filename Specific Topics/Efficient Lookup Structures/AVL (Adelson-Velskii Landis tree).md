AVL is a height-balanced [[Binary Search Tree]].

- The heights of left and right subtrees of *every* node differ by at most one
	- If at any time they differ by more than one, rebalancing is done to restore this property.

T is an AVL tree if T is a binary search tree *AND*
- Every node of T has a balance factor equal to 0, 1 or -1.
- Our balance factor is = height(L) - height(R)
- We keep our balance by making sure a node has a balance factor less than 1 or more than -1.

## Balancing

The tree is usually balanced from the bottom up (We check balance factor of each node from lowest node with a balance factor not in {0, 1, -1})
There are four possible scenarios

1. Left-left
	- A node has a balance factor +2 and
	- Its left child has a balance factor 0 or more

	- Rotate the left child to be parent of the subtree (pinch it up)
	- Any subtrees to the right of the pinched up node will be placed to the left of the node to the right of the pinched up node.
		![[AVLLeftLeft.png]]

2. Left-Right
	- A node has a balance factor +2 and
	- Its left child has a negative balance factor

	- Convert the tree into a left-left case by rotating the child instead.
	- We pinch up the node to the right of the negative balance factor and then place the left subtree of the right node to the right of the original negative balance factor node.
		![[AVLLeftRight.png]]
	- From this we can just perform operations for pinching the left-left case. In this case we would pinch up 20 to be the new parent, 24 would be the subtree to the right and we would place subtree B as the left child of 24.

3. Right-Right
	- Essentially a mirror of what we do with left-left.
	- Node has a balance factor of -2 and its right child has a negative or 0 balance factor
	- We pinch the right child up as the new parent.
	- We place the left child of the right child as the right child of the original parent node.
		![[AVLRightRight.png]]
4. Right-Left
	- Essentially a mirror of left-right
	- Node has a balance factor of -2 and its right child has a positive factor.
	- We convert this into a right-right case by pinching up the left child of the right child of the unbalanced node.
	- We also move the right child of the pinched up node to the left child of the parent that was moved down.
	- This is a right-right case.
	- From here we can just perform the same steps for Right-Right![[AVLRightLeft.png]]

## Complexity Analysis

### Time Complexity

#### Search algorithm
- Worst Case:
	- O(Log N) because the tree is always balanced
#### Insertion/Deletion in AVL tree
- Insert/Delete the element in the same way as in BST. This would take O(Log N) time to traverse to the correct position based on what its value is relative to the nodes it has traversed.
- Balance the tree if it has become unbalanced
- At most we have to balance O(Log N) nodes when we insert a value.
- Total cost of balancing after insertion/deletion is O(Log N) in worst case
- In order to get our balance factors quickly we can
	- Store the current height of the node with the node.
	- This allows us to quickly calculate the balance factor by using:
		- height(current.left) - height(current.right).
	- Heights are usually easy to update because we can recursively update them when we insert a node after a node with height 0.