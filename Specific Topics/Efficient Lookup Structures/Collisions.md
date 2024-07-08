A consequence of having more keys than indices in our table.

When many values are hashed to the same slot in our hash table.

The probability of collision can be mapped using:
- N items
- Table Size = M
- Probability of no collision can be shown as:
	- M/M \* (M-1)/M \* (M-2)/M \*.....\* (M+1-N)/M
	- This is:
		- M!/(M^N * (M-N)!)

## Handling collisions

We have two main ways of handling collisions

- [[Chaining]]
- [[Probing]]