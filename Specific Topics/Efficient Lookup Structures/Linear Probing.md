In case of collision, sequentially look at the next indices until you find an empty index.

![[HashTableProbing.png]]

h(k, i) = (h'(k) + c\*i) % M

where h'(k) is some hash function
i is how many times we have probed
k is the value we are probing for
c is any constant we wish to use (1, for example).
M is just what value we decide to divide by. Usually this is the hash table size.

## Operations

### Searching

- Look at index = h(key)
- If element not found at index, sequentially look into next indices until
	- you find element
	- reach an index which is NIL (This implies that the element was not put into the table as if the element was probed, it should replace the next NIL position).
- Worst Case Search Complexity:
	- In general for probing based tables we resize the table size once the load factor exceeds a certain value.
	- Load factor = number of elements in table/size of table.
	- This means the table is never full.
	- Still O(M) for search since the table could have load factor \* M elements and they could all be in one cluster.
	- A cluster is a collection of elements that are clumped up into one giant mass because they keep hashing to the same value and being added one after the other.
	- The more values start to cluster, the more collisions start to happen and the more clustering happens. This is a runaway exponential effect and can make performance deteriorate quickly.

### Deletion

With linear probing, if we delete we must consider the fact that elements that had the same hash when inserting might exist in the table in a probed location.

#### Methods to overcome this:
- We reinsert all values that come after the deleted value. This ensures we reprobe the hash table for proper sequencing.
- When deleting, instead of just deleting we mark it as an element for deletion. When we do any searches from then on, this marked element can be skipped. Any insertions from then on can simply replace the marked element with the inserted element.

## Problems with linear probing

- Collisions from nearby hash values tend to merge into big blocks.
- The lookup can then end up degenerating into a linear O(N) search at worst case.
- This is called primary clustering.