Sort the input array by selecting the next correct element and placing it in the sorted part of the array.

Loop Invariant: 

**arr\[1 .... i-1]** is sorted 
**AND**
**arr\[1 .... i-1] <= arr\[i .... N]**.

Time Complexity: O(n^2)
Space Complexity: O(n)
Auxiliary Space Complexity: O(1)

Not [[Stability|stable]]: It swaps non-adjacent elements.  

In-place sort as the auxiliary time complexity is O(1). 