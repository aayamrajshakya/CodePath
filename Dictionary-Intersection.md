*[[Unit 2 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Should I include entries if only the keys or only the values match, but not both?
  - No.  Both keys AND values must match.
- What if either dict is empty?
  - If either dict is empty, there will be no matches possible -- so you would return an empty dict.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Loop through each key in d1, check if it's in d2.  If so, check if their values match.  If they do, add to a list of matches.

```markdown
1) Create an empty dict for matches
2) Loop through each key in d1
  a) If the key is also in d2 AND both values match
    i) Add to matches dict
3) Return matches dict
```

## I-mplement

```python
def dict_intersection(d1, d2):
    result = {}
    for key in d1:
        if key in d2 and d1[key] == d2[key]:
            result[key] = d1[key]
    return result
```