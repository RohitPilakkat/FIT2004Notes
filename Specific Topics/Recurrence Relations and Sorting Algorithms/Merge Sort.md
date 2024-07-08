Sorts algorithm by recursively breaking down the input array into progressively smaller sections of the array to sort until it reaches a base case of 1 element. It then breaks down the recursion and sorts the array on the way up. 

Loop Invariants:
- A\[P......K-1] that contains (k-p) smallest elements of L\[1....n1+1] and  R\[1....n2+1].
- L\[i] and R\[i] are the smallest elements of the array that have not been copied back into A.
- Array A is the sorted result.

Time Complexity:
- Best Case/Worst/Average: O(n log(n))

Space Complexity: O(2n)
Auxiliary Space Complexity: O(n)

[[Stability|Stable]]: Yes

In-Place: No as its auxiliary space complexity is O(n) (It requires making a new array of n/2 size for each side of the split).