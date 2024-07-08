A lookup table allows inserting, searching and deleting values by their keys.


Elements of a table, in some cases, contain a key plus some other attributes or data.
The key might be a number or a string (eg. ID or authentication string).
It is usually something unique that unambiguously identifies a single element.
Elements can then be looked up using this key.

## Sorting Based Lookup

Keep the elements sorted based on their keys in an array (eg. sort by ID).

- Searching: O(Log N)
	- Use [[Binary Search Tree|binary search]] to find the key O(Log N)
- Insertion: O(N)
	- Use binary search to find the sorted location of new element - O(Log N)
	- Insert the new element and shift all larger elements towards the right - O(N)
- Deletion: O(N)
	- Search the key - O(Log N)
	- Delete the key - O(1)
	- Shift all the larger elements to the left - O(N)

This is a very basic approach. We can approach it in a better way using:
- [[Binary Search Tree|Balanced Binary Search Trees]]
- [[Hash Tables]]