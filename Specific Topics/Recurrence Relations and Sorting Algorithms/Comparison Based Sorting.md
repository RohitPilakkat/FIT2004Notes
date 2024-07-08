Sorts the algorithm by comparing items with each other

Examples of Comparison Based Sorting:
* [[Selection Sort|Selection Sort]]
* [[Insertion Sort]]
* [[Quicksort and Partitioning|Quick Sort]]
* [[Merge Sort]]
* [[Heap Sort]]

Algorithms that do not require comparing items with each other are called [[Non-Comparison Based Sorting| non-comparison sorting algorithms]].

Generalised Comparison Cost: O(1) complexity.

However this is not always true.

String Comparison:
- Worst-Case of comparing two strings is O(L) where L is the number of characters in the smaller string. This is because the computer goes through each character of a string to compare it.

Number Comparison:
- Generally we can assume that numbers are appropriately machine-word sized and comparison should take O(1). Theoretically for very large numbers the comparison would be O(digits).