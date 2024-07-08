None of the previous hashing schemes can provide a guarantee for O(1) searching at worst-case.

Cuckoo hashing might be able to:

- Searching: O(1) in worst case
- Deletion: O(1) in worst case
- Insertion: May be significantly higher but average cost is O(1)

## Idea

- Use two different hash functions hash1() and hash2() and two different hash tables T1 and T2 of possibly different sizes.
- hash1() determines index in T1 and hash2() determines the index in T2.
- Each key will be indexed in only one of the two tables.
- handle collision using the Cuckoo Approach.

## Cuckoo Approach

Kick the other key out to the other table until every key has its own table.

Values can keep kicking each other off the table until they find an empty spot.

At worst case, expected cost to insert N items is O(N) because it will keep kicking every item until it finds a suitable spot.

