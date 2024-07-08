To make counting sort more [[Stability|stable]] we can approach the data in a different way.

Very similar to [[Counting Sort]] however we want to make it stable.

We first construct the Count array in the same way.

Then we also construct a second Position array.

This position array is a cumulative tracker of where the position of the value should be.

The index matches what the value should be while the values at these indexes specify where these values will end by considering the count of the element. ![[Stable Counting Sort.png]]

We can then go through the input array and check where the value (For example (3, a) by looking at value 3) should go by checking the position array.

The first time this happens, 3 goes into position 2 in the output array. The value within the position array is then incremented by 1 indicating that the next 3 that is encountered should be placed one step later. The next time a value of 3 is encountered (In this case (3,c)), it will then be placed at position 3.

Counting Sort is now stable and keeps associated data intact

Time Complexity: 
- O(N+U) same as counting sort
Space Complexity:
- O(N+U) same as space complexity