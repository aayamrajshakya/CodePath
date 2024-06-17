*[[Unit 2 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Should I subtract entries if only the keys match, but not the values?
  - No -- only subtract when both keys AND values match.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Loop through each key in d1, check if it's in d2.  If not, add to a list of results.

```markdown
1) Create an empty dict for the result
2) Loop through each key in d1
  a) If the key is not in d2 OR has a different value
    i) Add key : value pair from d1 to results
  b) If the key is in d2, but has a different value
    i) Add key : value pair from d1 to results
3) Return results dict
```

## I-mplement

```python
def dict_difference(d1, d2):
    result = {}
    for key in d1:
        if key not in d2 or d1[key] != d2[key]:
            result[key] = d1[key]
    return result
```