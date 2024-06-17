*[[Unit 1 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Loop through a list of numbers, and if a number matches the target, add it's index to a results list.

```markdown
1) Create an empty list to hold the results
2) Loop through the indices of the input list
  a) If the element at that index matches the target, add the index to the results list
3) Return the results list
```

**⚠️ Common Mistakes**

- Be sure you are adding the INDEX of each match to your results list -- not the match itself!

## I-mplement

```python
def find_all_occurrences(lst, target):
    indices = []
    for i in range(len(lst)):
        if lst[i] == target:
            indices.append(i)
    return indices
```