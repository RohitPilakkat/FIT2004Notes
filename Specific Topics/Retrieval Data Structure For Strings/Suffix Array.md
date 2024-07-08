Suffix Array enables us to reduce the space complexity of sorted suffixes to O(N).

![[SuffixArray.png]]

Instead of storing an entirely separate, sorted array of substrings we can just store the IDs of where the substring starts in the sorted suffix array.

This reduces our space complexity (The original string + the sorted suffix array) down from O(N^2) to O(N) as storing the ID only requires O(N+N) which is O(2N) which is O(N).

## Reducing Construction Cost

We can implement Prefix Doubling to reduce the cost of construction

- Ranks
	- Tell us the relative order of strings
	- Only with respect to the chars which have been considered so far

### Basic Idea
- Generate suffixes
- Use ASCII values of first chars to set up ranks (First character only)
- Sort the strings on first 2 chars using ranks for first char
	- Sort the second char of substrings with the same rank (Same first character).
- Update the ranks
- Ranks now pertain relative to order of first 2 characters
- Sort the strings on first 4 characters using ranks for first 2 characters
	- Ranks now pertain to relative order of first 4 characters
- Keep going until we have sorted everything.
- This is a much quicker way to sort suffixes because:
	- If the current rank is smaller than the rank of another substring, we know this is a smaller value regardless of the current characters being checked since their preceding characters have given them a lower rank.
		- Comparison cost here is O(1) because we can instantly skip anything with different ranks.
	- If the current ranks are the same, the previous K characters must be the same.
		- The tie must be broken on the next k characters.


In this way, prefix doubling enables a construction in NLog(N) time
We can now compare prefixes in O(1) time