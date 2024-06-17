*[[Unit 2 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Can there be multiple peaks in the mountain list?
  - No. By our definition of mountain list, there will only ever be one peak.
- What if the list is empty?
  - The list will always have at least 3 elements.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Loop through each middle element and compare it to the element after.  If it's larger than the next element, we've found the peak.

```markdown
1) Loop through the middle elements of the list (skip the beginning/end)
2) Compare each element to the next element 
  a) If the next element is bigger, keep looking
  b) If the next element is smaller, return the current element
```

## I-mplement

```python
def peak_index_in_mountain_list(lst):
    for i in range(1, len(lst) - 1):
        if lst[i] > lst[i + 1]:
            return i
```
