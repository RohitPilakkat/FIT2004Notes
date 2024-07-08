- Hash Functions
	- Takes elements of a big (possibly infinite) universe and maps them to some infinite range.
	- One way to do this easily is using modulus as this can limit our range a good amount.
	- Simply finding the modulus however is a bad key since there might be a lot of clashing.
	- When using a%m the remainder when a is divided by m we get:
		- a value range of \[0...m-1].

## Major issues that arise from this method

- [[Collisions]]