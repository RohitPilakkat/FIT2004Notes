Assume that all elements are unique.
- Sort the list into groups of size five.
- Find the median of each group of five
- Find the median of these medians.
- We can use [[Insertion Sort]] to find the medians for each sublist if n<=5
- If more than 5, we can use [[Quickselect]] to find the median of each sublist.

