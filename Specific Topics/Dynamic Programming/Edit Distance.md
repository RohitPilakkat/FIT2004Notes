## Problem Definition

The words computer and commuter are very similar and a change of just one letter, p -> m will change the first word into the second.

The word sport can be changed into sort by the deletion of p or equivalently sort can be changed into sport by the insertion of p.

- Notion of editing provides a simple and handy formalisation to compare two strings.

Edit Distance: 
- The goal is to convert the first string (i.e, a sequence) into the second through a series of edit operations.

The permitted edit operation are:
- Insertion of a symbol into a sequence
- Deletion of a symbol from a sequence
- Substitution or replacement of one symbol with another in a sequence.

Edit Distance between two sequences.
- Edit distance is the minimum number of edit operations required to convert one sequence into another (assuming that all operations have equal costs).

For example:
- Edit distance between computer and commuter is 1.
- Edit distance between sport and sort is 1.
- Edit distance between shine and sings is ?
- Edit distance between dnasgivethis and dentsgnawstrims is?

Basically edit distance is the minimum number of operations we need to change S1 into S2.

Some applications of edit distance:
- Natural Language Processing:
	- Auto Correction
	- Query Suggestions
- Bioinformatics
	- DNA/Protein sequence alignment.

## Methodology

We want to convert s1 to s2 containing n and m letters, respectively.

We start checking from the last character in the sequence and determine what to do there.

### Determination:

#### Same Characters
- If the characters \[n] and \[m] are the same, we can say that the edit distance between \[0...n] to \[0...m] would be the exact same as the edit distance between \[0...n-1] to \[0...m-1].
#### Characters do not match
- If \[n] and \[m] are not the same, we must make a change.
- We can choose to insert, replace or delete.
##### Replace
- We can instead start trying to looking at viable transformations for s1\[0...n-1] to s2\[0....m-1].
- After we have found a viable transformation for the previous characters, we can then simply replace the correct character to the end of the solution with the mismatched character we were originally looking at.

##### Insert
- We can instead start trying to look for a viable transformation for s1\[0....n] to s2\[0....m-1].
- After we have found a viable transformation for the previous characters, we can then simply add it to the end of the correct solution we have gotten for the previous sequences of characters.

##### Delete
- We can instead start trying to look for a viable transformation for s1\[0...n-1] to s2\[0...m].
- We are looking for viable options where we simply delete the mismatched character.
- When finding solutions for this sequence, we are essentially disregarding any solutions that might include a sequence that includes the mismatched character. This is equivalent to deleting it from the sequence.

We then take the minimum of these operations (The minimum number of operations to reach the previous sequence that we are checking for each operation).



The idea is that we are slowly figuring out the edit distance for every variation of operations from empty strings to the full string. These are the subproblems that form the full solution.![[EditDistanceBottomUp.png]]

This is a bottom up method, however we can do a similar thing with a Top-Down solution by recursively checking for the minimum between all 3 operations 

min({s1\[n-1], s2\[m-1]}, {s1\[n-1], s2\[m]}, {s1\[n], s2\[m-1]}).

When we reach a base case we can collapse the recursion and go back up while slowly filling in the table. Any future calculations of subproblem answers can then instead just look at the table and skip anymore recursive calls entirely.

## Complexity Analysis

### Time Complexity

a = s1 length
b = s2 length
Therefore time complexity is
O(ab). This is because we have to check every single spot of the solution table for all variations of answers. This is much better than brute-forcing it however as we skip any repeated calculations.

### Space Complexity

Our solution requires a table of size a x m therefore our space complexity is a x m.