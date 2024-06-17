*[[Unit 2 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Can either dictionary be empty?
  - Yes.  In this case -- you won't find any matches, so your function should return an empty list.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Loop through one dict and make a list of any keys that are also in the other dict.  

```markdown
1) Create an empty list to hold common keys
2) For each key in dict1
  a) If the key is also in dict2, add to common keys
3) Return common keys
```

## I-mplement

```python
def common_keys(dict1, dict2):
    common = []
    for key in dict1:
        if key in dict2:
            common.append(key)
    return common
``