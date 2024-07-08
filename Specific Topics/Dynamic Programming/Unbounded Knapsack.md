## Problem Definition

Given a capacity C and a set of items with their weights and values, you need to pick items such that their total weight is at most C and their total value is maximised. What is the maximum value you can take? in unbounded knapsack, you can pick an item as many times as you want.

## Example

What is the maximum value for the example given below given capacity is 12Kg?
![[UnboundedKnapsack.png]]

## Overlapping Subproblems

What do we store in our memo array?
- Memo\[i] = Most value with capacity at most i.

## Optimal Substructure

If we know the optimal solution to smaller subproblems, we can build up a solution to a larger problem made of those subproblems.
- For each possible item choice, find out how much value we could get by checking through the memo table and see what leftover optimal values we can acquire using the leftover space we have.

## Process

Let us assume try the recursive top-down approach with a base case first

### Base Case

Our base case is when the capacity is 0Kg. Our value would then be, simply, $0.

### Deduction Phase

We can say that at capacity 1Kg we can have a maximum value of $40 as we can only hold 1 item of 1Kg (D).

We can say that at capacity 2Kg we can have a maximum value of $80 as we can only hold 2 items of 2kg (2D).

We can say that at capacity 3Kg we can have a maximum value of $120 as we can only hold 3 items of 3kg (3D).

We can say that at capacity 4Kg we can have a maximum value of $160 as we can only hold 4 items of 4Kg (4D).

At capacity 5Kg we now have a new option, B. B is exactly 5Kg and with a value of $350. This would take up all the capacity. However we can also have the option of picking D that has 1Kg for $40. If we take B, our maximum value is capped at $350. If we pick up D we have capacity for 4 more. If we go back to our table and check each case where MaxValue\[5-1] we will see that we can now hold $40 + $160 = $200.

We can see this value is less than just taking one 1B so our solution for MaxValue\[5] is (1B).

However at capacity C, even though we now have C (6Kg) available, we can see that the value of 6Kg is $180. C will take up all the capacity of the bag and therefore limit us to a max of $180. If we check our other values, B and D, we can first check B = 5Kg. With 5Kg we would have $350 + MaxValue\[6-5]. MaxValue\[1] would be $40 so our total maximum value is $390 (1B1D).

We can further check this with D = 1Kg. If we check $40 + MaxValue\[6-1] we can see that at MaxValue\[5] our max value, from the memo table, is again B, 5Kg, for $350. We get the same result (Because these are equivalent selections made).

So our final solution for MaxValue\[6] is (1B1D) for a max value of $390.

### Recurrence Relation

MaxValue\[c] = 
- 0, if c < wi for all i,
- max(1<=i<=n, wi<=c) \[vi + MaxValue\[c-wi]] otherwise

Overlapping Subproblems:
- memo\[i] = most value with capacity at most i
- optimal substructure is recurrence relation.

![[KnapsackBottomUp.png]]

![[KnapsackTopDown.png]]

## Complexity Analysis

### Time Complexity

O(NC)
- We are checking the memo table C times (The capacity we are aiming for) and checking the memo table N times for the number of options.

### Space Complexity

O(C + N)
- We have an initial table constructed based on the maximum capacity we are aiming for (C) and also using a table that tracks the costs of each item (N).