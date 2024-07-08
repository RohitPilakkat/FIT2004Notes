Prefix [[Trie]]s are very useful for quickly looking up whole words but more generally, prefixes of words.

A prefix of a word s\[1...m] is s\[1...i] where 1<=i<=m
A suffix of a word s\[1...m] is s\[i...m] where 1<=i<=m


Any substring of a word is a prefix of some suffix.

A substring of s\[1...m] is s\[i...j].

- s\[i...j] is a prefix of s\[i...m] (which is a suffix of s\[1...m])
- To be able to efficiently search substrings we can make a prefix trie of suffixes.![[suffixTrie.png]]

This way we can search for any substring in a string by following the characters to see if it doesn't terminate prematuraly.

For example, if I search for the substring "efe" in this trie, I will be able to find it as it does not prematurely terminate.

However if I search for the substring "eff" this will terminate as there is only a node with e after f.

## Time Complexity

O(M) where M is the length of the substring

## Number of occurrences

We can find this by counting the number of leaf nodes with ('$") in the subtree of the node that we found the final character of our substring at.

## Space Complexity

O(N^2)



A more compact way of storing a Suffix Trie is a [[Suffix Tree]]
