This uses a binary heap (A binary tree where layers are 'completed' first before adding more nodes).

Loop Invariants:
- Subarray A\[1...i] consists of the smallest elements of the original array A arranged in a max-heap structure.
- The max-heap structure ensures the largest element of the heap is at the root.

Time Complexity:
- O(N Log N).
	- Heap build takes O(N)
	- Heapify (Pushing the max element to the root) takes O(Log N) times

Auxiliary Space Complexity:
- If the heap is directly build within input array.
	- O(1)
- If a separate heap is made
	- O(N)

Space Complexity:
- With an iterative heapify() we have O(N)
	- O(N) is the space of the input array

[[Stability|Stable]]: No as we have to swap the place of A\[i] with A\[i+1] for finding max within the heapify process.

In-Place: Yes if we build the heap within the input array. Otherwise No