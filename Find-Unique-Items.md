*[[Unit 2 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Find items unique to one list, and categorize based on which list they were unique to.

```markdown
1) Create an empty dict for unique 
2) For each item in list_a:
  a) If item is not in list_b, map item -> True in unique dict
3) For each item in list_b:
  a) If item is not in list_a, map item -> False in unique dict
4) Return unique dict
```

## I-mplement

```python
def find_unique_items(list_a, list_b):
    unique = {}  # Initialize an empty dictionary to store unique items and their origin (True for list_a, False for list_b)

    # Check for items in list_a not in list_b
    for item in list_a:
        if item not in list_b:
            unique[item] = True

    # Check for items in list_b not in list_a
    for item in list_b:
        if item not in list_a:
            unique[item] = False

    return unique
``` 