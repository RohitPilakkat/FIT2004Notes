## Problem Definition

A country uses N coins with denominations {a1, a2, ...., an}. Given a value V, find the minimum number of coins that add up to V.

### Problem Example

- Suppose the coins are {1, 5, 10, 50} and the value V is 110. The minimum number of coins required to make 110 is 3 (two 50 coins, and one 10 coin).

- Greedy Solution (e.g. picking the biggest possible coin first) does not always work. E.g., Coins = {1, 5, 6, 9}.
	- The minimum number of coins to make 12 using the above greedy solution is
		- 4 coins (9+1+1+1)
	- The optimal solution is how many coins?
		- 2 coins (two 6 coins)
- What is the minimum number of coins to make 13? (Optimal solution)
	- 3 (two 6 coins and 1 coin)

## **GREEDY SOLUTION DOESN'T ALWAYS WORK**

We can instead using dynamic programming to figure this out.

### Overlapping Subproblems

What can we memoise?

We want to know the minimum number of coins which add upto V so let's try:
- MinCoins\[V] = {The fewest coins required to make exactly $V}

### Optimal Substructure

To find the optimal substructure we first consider the base case.

#### Base Case

In this case, to make $0 we require 0 coins so MinCoins\[0] = 0.

Assume we have optimal solutions for all v < V stored in MinCoins\[0 ... V - 1].

### Deduction phase

![[DPCoins.png]]

When checking how many coins we need to get a value of 12, we go through each possible coin we can use. We can first check 9. If we check 9, we only need the optimal solution for 12-9 which is 3. The optimal solution to get 3 is another 3 coins. (1, 1, 1). This means we need a total of 4 coins if we use 9 as our first value.

However if we pick 6 instead, we need to find the optimal solution for 12-6 which is MinCoins\[6]. The optimal solution to get 6 is 1 coin, which is coin with value 6 therefore we only need 2 coins. This is the optimal solution for getting 12.

We can keep checking the next few values to make sure this is the optimal solution.

If we take 5, we can check what the optimal solution for MinCoins\[12-5] would be. This is MinCoins\[7] which is 2. This would make a total of 3 coins which is not the optimal solution so we can disregard this.

If we take 1, we can check what the optimal solution for MinCoins\[12-1] is. This is again 2. This would make a total of 3 coins again which is again not an optimal solution.

Therefore our optimal solution, by using memoisation, is 2 coins by taking 2 6 value coins.

### Bottom Up (Iterative)

![[DPCoinsBottomUp.png]]

### Top Down (Recursive)

![[DPCoinsTopDown.png]]

