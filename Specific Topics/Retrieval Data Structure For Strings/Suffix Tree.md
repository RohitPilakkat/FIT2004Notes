A Suffix Tree is a compact [[Suffix Trie]].

We can compress the branches by merging nodes that only have one child.

Total complexity is still the same as we are storing the same number of letters.

![[suffixTree.png]]

## Space Complexity

If we replace every substring with numbers (x, y) where x is the starting index of the substring and y is its length

eg
- ferrer$ is represented as (3, 7)
- rer$ is represented as (6,4)
![[SuffixTreeCompact.png]]

- Every internal node has atleast 2 children
- There are exactly n+1 leaves
- There are at most n internal nodes
- Suffix trees are O(N) space

## Time Complexity

- Inserts O(N) suffixes
- Insertion cost of each suffix is linear to the size of the suffix
- Average suffix size is O(N)
- Compressing the trie requires traversing it O(N^2)

Thus total time complexity to construct the tree is O(N^2).