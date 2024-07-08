For each hash value, we have a separate data structure which stores all items with that hash value.

Essentially we are creating a chain of values that have the same hash value.

If there are already some elements at the hash index:
- Add the new element in a list at the array\[index].![[HashTableChaining.png]]

Lookup/Search:
- Index = hash(key)
- Search in the list at Array\[index]

Deleting an element
- Search for the element
- Delete it

Assume that M is the size of the hash table and that the load of the table is < C

Assume that our hash function distributes our keys uniformly over our hash table.

There are at most c\*M items already in the table distributed amongst M chains.

The average chain has c < 1 items in it

The average time complexity of an insert operation is O(1).

We can use any data structure as our chains.

A simple example could be a linked list however something better might be:

- [[Binary Search Tree]]
- Another [[Hash Tables]] (FKS Hashing)