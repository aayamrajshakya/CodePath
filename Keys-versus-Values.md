*[[Unit 2 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Will both the keys and values always be integers?
  - Yes.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Find the sum of all keys, the sum of all values, then print a result based on their comparison.

```markdown
1) Find the sum of all keys
  a) First, get all keys as a list
  b) Next, find the sum of that list
2) Find the sum of all values in the same way
3) Check which is larger, and print the result accordingly
```

## I-mplement

```python
def keys_v_values(dictionary):
    # Calculate the sum of all keys
    sum_of_keys = sum(dictionary.keys()) # can also use a loop
    
    # Calculate the sum of all values
    sum_of_values = sum(dictionary.values()) # can also use a loop
    
    # Determine which sum is greater or if they are equal
    if sum_of_keys > sum_of_values:
        return "keys"
    elif sum_of_values > sum_of_keys:
        return "values"
    else:
        return "balanced"
``` 

*Note: You might have solved this problem by using loops to sum up the `.keys()` and `.values()` lists.  That will also work, but using the provided `sum(list)` function in python simplifies your code.*