Sort an array of numbers assuming each number has K digits.
- Use a [[Stability|stable]] sort to sort them on the 1st digit (Least significant digit)
- Sort based on 2nd digit
- Keep sorting until we have sorted till Kth digit (Most significant digit)
This sort uses the fact that a number's size is bounded by its most significant digit.

For the purpose of sorting the numbers based on the digit itself, we must use a [[Stability|stable]] sorting algorithm such as [[Counting Sort]].
Counting Sort is perfect for this as we can easily assume a max value for U. For numbers of base 10 we know that the maximum U would be 10 (values from 0-9). For numbers of base 2 (binary) we can assume that U would be 2 (0, 1).

Time Complexity: 
- Based on the complexity of the stable sort we use for sorting based on digit
- If we use [[Counting Sort]] for example:
	- Using a base that is less than the number of elements in the original list such as a low value like 2 (binary)
	- We can have a counting sort time complexity of O(N)
	- We would have to call counting sort for every digit, d, in the array.
	- Therefore best-case complexity is:
	- O(d * N). 
	- If we assume that the number of digits is less than the number of values we have to sort we can say that complexity is there O(N)
	- Average case:
		- O(d * (N + b)) where b is the base that we decide to use.

Space Complexity:
- Counting Sort would have a space complexity of O(N + b) where b is the base we use.
- If we assume that the base is a very small number, it is likely O(N) instead.