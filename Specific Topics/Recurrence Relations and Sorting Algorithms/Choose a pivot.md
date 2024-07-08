Choosing a random pivot for [[Quicksort and Partitioning|quicksort]] (Or quick select) will give us, at worst case, a time complexity of O(N^2).

If we can find a good pivot within O(N) then we can have a quicksort worst case time complexity of O(N log N).

[[Quickselect]] can be used to return the Kth smallest element in an array. However at worst-case this is still O(N^2) so does not improve our quicksort algorithm. It actually makes it *worse* by changing worst-case from O(N^2) to O(N^2 Log(N)).

Instead we can try [[Median of Medians]] with quickselect in order to improve our worst-case to O(N).

## Interesting Note

Taking the average of a sequence of elements is usually a decent enough idea for finding a good pivot.

However there are some inputs where this still causes a worst-case scenario of O(N^2).

An example is where we have F(i) = (i!) for 1<=i<=n.

The average for this sequence would be slightly bigger than (n-1)!.

This would mean that the only element bigger than the average is now (n-1)!.

This would lead to a worst case of O(N^2) for this set of inputs.
