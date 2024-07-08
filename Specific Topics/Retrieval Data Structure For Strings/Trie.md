A trie is a multi-way tree where the number of branches is the size of the alphabet.

NumBranches = 2 for binary
NumBranches = 26 for English letters
NumBranches = 4 for DNA

In a standard Trie, all words with the shared prefix fall within the same subtree/subtrie.
It is the shortest possible tree that can be constructed such that all prefixes fall within the same subtree.

## Insertion

### Example

A Trie that stores:
- baby
- bad
- bank
- box
- dog
- dogs
- banks

We use $ to denote the end of a string

Inserting procedure:
- Start from the root node
- For each character c in the string
	- if a node containing c exists
		- move to the node
	- Else
		- Create the ndoe
		- Move to it

![[TrieStandard.png]]

Think of it as making a tree based on what character we have reached and what the next character should potentially be.

## Search

Steps
- Start from root node
- For each character c in the string (including $)
	- If a node containing c exists
		- Move to the node
		- if c == $
			- Return "Found"
	- Else
		- Return "Not found"

#### Time Complexity
For loop runs O(M) times where M is the number of characters in the string.


## Prefix Matching

Prefix matching returns every string in text that has the given string as its prefix.

- Start from the root node
- For each character c in the prefix
	- If a node containing c exists
		- Move to the node
	- Else
		- Return "not found"
- Return all strings in the subtree that are rooted at the last node we have found.

### Advantages

- A better search structure than a binary search tree with string keys
- A more versatile search structure than hash table
- Allows lookup on prefix matching in O(M) time where M is the length of prefix
- Allows sorting collection of strings in O(MN) time where MN is the total number of characters in all strings

### Disadvantages
- On average Tries can be slower than hash tables for looking up patterns/queries
- Wastes spaces, since even when a node has few children, you need to create an array of size alphabet

## Properties

- The maximum depth is the length of longest string in the collection
- Insertion/Deletion/Lookup operations take time proportional to the length of the string/pattern being inserted, deleted or searched.
- We waste a lot of space if
	- Each node has a pointer per symbol in the alphabet
	- Deeper nodes typically have mostly null pointers
- Can reduce total space usage by turning each node into a linked list or binary search tree but this trades time for space (As an array can be checked in O(1) time while a linked list/binary tree are O(C) or O(Log(C) respectively where C is the total number of characters possible).
