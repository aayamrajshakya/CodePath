*[[Unit 2 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Will either list ever be empty?
  - Potentially, yes.  Your code should allow for this.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Take turns looking for each element of the smaller list, in order, until we either find all elements or run out of room to search.

```markdown
1) Start at the beginning of the sequence (second list)
2) Loop through the first list, and each time:
  a) If we are out of numbers in the sequence, return true
  b) Otherwise, if the current sequence value matches,
     move on to the next sequence index
3) If the loop finishes, we didn't match them all, so return false
```

## I-mplement

```python
def is_subsequence(lst, sequence):
    seq_idx = 0
    for num in lst:
        if seq_idx == len(sequence):
            return True
        if sequence[seq_idx] == num:
            seq_idx += 1
    return False
```