A table (array) that contains elements that are indexed with a unique value (Such as ID).

Searching the table is simply returning the value at the value we have used to index it which gives us O(1) lookup complexity.

If we want to index using non-integers we must come up with a way to represent these unique values in an appropriate way.

The values we generate from this method can potentially be large and spread out (huge range).

If we want a table with a size with the larger value our hash can produce, this may be an unbounded value which is impossible.
## Methods of indexing

- [[Direct-Addressing]]
## Issues that can arise from indexes

- [[Collisions]]


### Methods to address collision issues

- [[Chaining]]
- [[Probing]]


