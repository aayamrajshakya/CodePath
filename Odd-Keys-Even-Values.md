*[[Unit 2 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Will all keys and values in the dict be integers?
  - Yes, unless the dict is empty.
- What should my function do if the dict is empty?
  - In that case, it should return 0.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Loop through the dict, and if the key is odd and value even, add the key to an output list.

```markdown
1) Results list starts empty
2) For each key and value in the input dict
  a) If the key is odd and value even, add key to results
3) Return results
```

**⚠️ Common Mistakes**

- Only add the key to the results list, not the value!
- A number is even when it is evenly divisible by two. How can we check that in python?


## I-mplement

```python
def odd_keys_even_values(dictionary):
	  result_keys = []
    for key, value in dictionary.items():
        if key % 2 != 0 and value % 2 == 0:
            result_keys.append(key)
    return result_keys
``` 