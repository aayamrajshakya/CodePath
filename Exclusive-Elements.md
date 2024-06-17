*[[Unit 3 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Loop through each list, and if the element isn't in the other list, add it to exclusives.

```markdown
1) Create empty list of exclusives
2) For each element in lst1:
  a) If the element is not in lst2, add to exclusives
3) For each element in lst2:
  a) If the element is not in lst1, add to exclusives
4) Return exclusives
```

## I-mplement

```python
def exclusive_elements(lst1, lst2):
    exclusive = []
    for item in lst1:
        if item not in lst2:
            exclusive.append(item)
    for item in lst2:
        if item not in lst1:
            exclusive.append(item)
    return exclusive
```