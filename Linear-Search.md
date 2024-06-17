*[[Unit 1 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Are all elements in the list integers?
  - Yes.
- Can the list be empty?
  - Yes.  In that case, your function should return -1.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Create a function that finds the index of a target element in a list of numbers.

```markdown
1) Loop from 0 to N, where N is the length of the list - 1
2) For each index
  a) Get the value of the list at that index
  b) If the value matches our target, return that index
3) If the loop finishes, no match was found, so return -1
```

## I-mplement

```python
def linear_search(lst, target):
    for i in range(len(lst)):
        if lst[i] == target:
            return i
    return -1

print(linear_search([1, 4, 5, 2, 8], 5))  # Output: 2
print(linear_search([1, 4, 5, 2, 8], 10)) # Output: -1
```