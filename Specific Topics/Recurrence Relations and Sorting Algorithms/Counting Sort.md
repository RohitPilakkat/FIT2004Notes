[[Stable Counting Sort]]


- Find the maximum integer in the array.
- Create an empty array "count" with size of maximum integer with each value initialised to 0.
- For each unique value found in the input, we increment the number in count. count\[value]+= 1.
- Basically tracking how many times an integer appears in an array and recreating the array based on this.

Time Complexity:
- O(N+U) where U is the size of the count array
Space Complexity:
- O(N+U)

[[Stability|Stable]]: No. This is because the algorithm merely counts the number of times the integer shows up and then recreates the correct array but does not actually track what exactly any associated data might be (Such as a key or a pointer to another structure in a tuple).


If we have a known number of elements to count, such as the alphabets (Max of 26 unique values) then we can disregard U in complexity calculations as the algorithm does not then scale with the count array length as it will always be 26.

Therefore in that case:
Time Complexity:
- O(N)
Space Complexity:
- O(N)

Counting sort is very efficient when U is very small (e.g O(N) when U<=N)
However Count Sort can be very inefficient when U >> N.