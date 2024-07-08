The algorithms we have seen determine optimal values:
- [[Coins Change]]
- [[Unbounded Knapsack]]
- [[Knapsack01]]
- [[Edit Distance]]

How do we construct optimal solutions that gives the optimal value:

i.e how do we reconstruct the optimal solution that we want instead of just finding the optimal solution?

There can be multiple optimal solutions and our goal is to return atleast one of them.

Two strategies can be employed:

- [[Decision Array|Create an additional array recording decision at each step]]
- [[Backtracking]]

### Comparison between backtracking and decision array

### Space Usage
- Backtracking requires less space as it does not require creating an additional array
- However space complexity is the same, i.e O(CN) == O(2^b N) for Edit Distance
### Efficiency
- Backtracking requires to determine what decision was made which costs additional computation (More backtracking, more computations).
- However time complexity is the same i.e O(CN) == O(2^B N) for Edit Distance.
[[Knapsack01||Note that the simple space saving trick discussed can only be used when the solution does not need to be constructed.]]
