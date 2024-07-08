Unlike [[Linear Probing]] that uses fixed incremental jumps (+c jumps), quadratic probing uses quadratic jumps.

Quadratic Probing: h(k, i) = (h'(k) + c\*i + d\*i^2) %M

Where C and D are random constants.

Quadratic probing is not guaranteed to probe every location in the table.
- An insert could fail while there is still an empty location
- It can be shown that with prime table sizes and load factor <0.5, quadratic probing always finds an empty spot.
- Therefore we make sure to resize when load factor = 0.5

## Searching and Insertion

We follow the same strategy as [[Linear Probing]] for these methods.

## Deletion

In [[Linear Probing]] each element k may be a part of a probe chain but the previous position in the chain will always be 1 (or c) positions before k, and the next position in the chain will be 1 (or c) positions after k.

For quadratic probing an element may be part of many, separate probe chains.

Which elements do we re-insert?

Instead of reinserting (method 1 of deletion for Linear Probing) we can instead mark them for deletion (lazy deletion) like in method 2 for Linear Probing Deletion.

When we do look ups, we do not return any marked elements (We move past them). 
When we do inserts, we insert and replace the marked element we find with the same hashed/probed location.


## Problems with Quadratic Probing

- Quadratic Probing avoids primary clustering however if two elements have the same hash index (e.g h'(k1) = h'(k2)), the jumps are the same for both elements.
- This leads to a milder form of clustering called secondary clustering where chains start to form in spots further away from our original hash location. This isn't as big of an issue as primary clustering however can still cause performance loss.

One way to deal with this is [[Double hashing]].
