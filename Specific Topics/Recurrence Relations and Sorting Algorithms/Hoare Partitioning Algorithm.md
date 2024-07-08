A partitioning algorithm is a very simple method of partitioning the array.

Steps:
- [[Choose a pivot]]
- Swap the pivot with the left element.
- Pointer Left points at second element from left
- Pointer Right points at last element (Right most)
- Pointer Left moves towards right until it points to an element > pivot
- Pointer Right moves towards left until it points to an element < pivot
- Swap the elements pointed at by Left and Right pointers.
- Repeat until Left Pointer passes Right Pointer.
- Finally swaps pivot back with the element pointed at by Right Pointer

Pros:
- Each element only swapped once (except pivot)
- Simple idea
- Simple invariant (Elements A(1...i) are smaller than pivot, elements A(end-i...end) are bigger than pivot)
Cons:
- Tricky to implement without bugs
- Not stable
- Performs badly when there are many elements equal to the pivot.