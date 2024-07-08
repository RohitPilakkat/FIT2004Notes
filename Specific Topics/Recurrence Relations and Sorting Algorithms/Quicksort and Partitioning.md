Essentially opposite of mergesort. 
We sort the current array around a pivot and then break it down into sub arrays and sort again until we have sorted all partitions down.

- Choose a pivot **p**
- Place smaller elements to the left of pivot, place larger elements to the right of pivot.
- Apply quicksort to either sides of the pivot.
Some methods to partition the elements:
- [[Hoare Partitioning Algorithm]]
- [[Dutch National Flag Partition]]

Time Complexity:
- Best Case: O(N Log (N))
- Worst Case: O(N^2)
- Average Case: O(N LogN)

[[Choose a pivot|Improving worst case time complexity can be done by choosing an appropriate pivot]]

With an improve quicksort, we have worst-case of quicksort as:
O(NLogN).

However in practice it might be better to just use a random pivot as the chance of getting a bad pivot are much lower than the overall time it takes to always find a good pivot using median of medians quickselect.

