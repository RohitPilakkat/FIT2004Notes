We can use two different hash functions:
- One to determine initial index
- One to determine the amount of jumps

h(k, i) = (hash1(key) + i\*hash2(key)) % M.
