*[[Unit 2 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Will all dictionary values be integers?
  - Yes.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Given a dictionary with all-integer values, add up all values that are even.

```markdown
1) Sum variable starts at 0
2) For each value in the dictionary's values:
  a) If the value is even, add it to the sum
3) Return the sum
```

**⚠️ Common Mistakes**

- You might be tempted to write a more complex loop using keys, but Python provides a way to get a list of just the `values` for the dictionary.

## I-mplement

```python
def sum_even_values(dictionary):
    sum_even = 0
    for value in dictionary.values():
        if value % 2 == 0:
            sum_even += value
    return sum_even
``` 