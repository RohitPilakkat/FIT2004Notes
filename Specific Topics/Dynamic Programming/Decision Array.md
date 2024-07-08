This is a way to track our steps to get an optimal solution so we can recreate the optimal solution.

#### Steps

- Make a second array of the same size
- Each time you fill in a cell of the memo array, record your decision in the decision array.
- Going right on the array (Or coming from the left) is insert.
- Going down (or coming from up) is delete
- Going down and right (or coming from up and left) is replace or do nothing.
- This is very similar to the table we have constructed in [[Edit Distance]].

![[decisionArrayEditDistance.png]]

This is an example of a decision array for edit distance.

By looking at the keywords in the decision matrix we now know how to recreate the solution.

Delete means we have come from up (So we go up to find the previous instruction).
Insert means we have come from left (So we go to the left to find previous instruction).
Replace or doing nothing means we have come from the top left (So we go top left to find previous instruction).