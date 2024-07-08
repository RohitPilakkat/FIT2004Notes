## Problem definition

Same as [[Unbounded Knapsack]] except that each item can only be picked at most once.

### Example

What is the maximum value for the example given below given capacity is 11Kg?![[zero1knapsack problem.png]]

## Difference from unbounded

If we pick an item X, giving us a remaining capacity R, we have to somehow make sure that X is not part of the optimal solution to our new subproblem of size R.

We can have two axes on which we think about these subproblems.

- Capacity
- Which items are part of the subproblem.
## Base Case

Capacity is MaxVal\[0]. In this case, we would have no items.

## Inductive Cases

We must make a 2 dimensional table that can track what the maximum solutions would be with increasing sample sizes.

i.e we must be able to track what the solution would be going from an available choice of just {A} to {A, B} to {A, B, C} to {A, B, C, D}
![[zero1knapsack2dtable.png]]

Here we can see that with no set, our solutions would be nothing all the way to C.
With just A we can only start having solutions from 6 because A has a weight of 6. This is the only choice available to us at that point and we can only take one of them.

When given a choice between A and B, we can have solutions starting from 1. At 6, the best choice we can make is A since it will take all the space in the bag and outvalues 1B.

At 7 however we can see that because we have one more spot left for an item of weight 1Kg, and B is of 1Kg, our solution can include both A and B therefore it becomes $270.

When increasing our solution sample size to {A, B, C} we can see this change once more where our solution at 5Kg can include C. C outweighs B and therefore that is the best solution. At 6Kg, since C+B can outweigh just A that is our optimal solution.

When increasing our solution sample size to {A, B, C, D} and checking for 11Kg we must first look at what the solution is like when disregarding D. If we disregard D, our solution is $580 (A+C) in the memo table at MaxValue\[11]\[3]. When including D, we can take D (9kg) and then also add the value we get from MaxValue\[11-9]\[3] to check what the solution is with capacity of 2Kg when only looking at A, B, C.

The answer for this is 550+40 = 590. As this is a bigger value than the solution with just A, B and C we can place this value as the answer for the MaxValue at 11Kg for the sample size {A, B, C, D} at MaxValue\[11]\[4].

## Complexity Analysis

### Time Complexity

O(NC)
- Filling each cell is O(1) since it is a max of 2 numbers however we must traverse this table N tmies (number of times) for C times (capacity of the knapsack).

### Space Complexity

O(NC)
- We are constructing a NxC table to keep track of the memosiation.
- Technically we can reduce the space complexity to O(C) by discarding rows that have been completed when they are not needed anymore (The next row is completed).
- However this does not work for top-down solutions as we don't know the exact order of solving subproblems (We can't just delete all the solutions that we don't need since we might need them for future sub-problems).
- This also cannot be used when we want to reconstruct a solution (Such as showing exactly which items we are picking).