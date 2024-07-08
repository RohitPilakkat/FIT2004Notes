Optimisation technique used in computer science

- Divide a complicated problem by breaking it down into simpler subproblems in a recursive manner and solve these.
- This is distinct from "divide and conquer" because:
	- Overlapping subproblems:
		- The same subproblems needs to be used multiple times
	- Optimal substructure:
		- Optimal solutions to subproblems help us find optimal solutions to larger problems (Solutions are made up of smaller, easier to find solutions).

### General Solution

Assume you already know the solutions of all sub-problems and have memoized these solutions (Overlapping subproblems).
- Eg: Assume you know Fib(i) for every i < n.

Observe how you can solve the original problem using memoized solutions (Optimal substructre).
- Eg: Fib(n) = Fib(n-1) + Fib(n-2).

Solve the original problem by building upon solutions to the sub-problems.
- Eg: Fib(0), Fib(1), Fib(2), ...., Fib(n).

There are usually two approaches to a DP problem:
1. Bottom Up: We iteratively solve from a base case and build up to the final solution.
	- Space-saving tricks can be applied to reduce space complexity (Don't have to rely on recursion stack).
2. Top Down: We break down a problem from its final case to the base case and recursively solve until we reach the final solution. This approach generally using a memoisation table to memorise values of previously solved sub-problems.
	- Top down may save some computations (e.g some smaller subproblems may not need to be solved) 
## Traditional DP Problems

1. [[Coins Change]]
2. [[Unbounded Knapsack]]
3. [[Knapsack01]]
4. [[Edit Distance]]
5. [[Constructing Optimal Solution]]
