*[[Unit 2 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What will be the output of this function?
  - The function should return the new map (a dictionary).

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Convert a list of values to a map (or dictionary) of indices -> values.

```markdown
1) Create an empty map (dictionary)
2) The current_index starts at 0
3) For each value in the list
  a) Add the current_index : value pair to the dictionary
  b) Increment the current_index by 1
4) Return the map
```

## I-mplement

```python
def index_to_value_map(lst):
    index_value_map = {}
    
    for index in range(len(lst)):
        index_value_map[index] = lst[index]
    return index_value_map
``` 