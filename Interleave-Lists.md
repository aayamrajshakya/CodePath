*[[Unit 3 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Loop from 0 to the longer length, and if valid, add an element from each list at that index,

```markdown
1) Create an empty list for results
2) Find the length of the longer list
3) For each index from 0 to the longer length:
  a) If index is valid in lst1, add that element to results
  b) If index is valid in lst2, add that element to results
4) Return the results list
```

**⚠️ Common Mistakes**

- You might be tempted to write two different versions of the same code, one for when lst1 > lst2, and one for the opposite.  Try to think of a way to write one block of code that works in both cases!

## I-mplement

```python
def interleave_lists(lst1, lst2):
    result = []
    
    lst1_len = len(lst1)
    lst2_len = len(lst2)
    length_of_longest_list = max(lst1_len, lst2_len)
	  
    for i in range(length_of_longest_list):
        if i < lst1_len:
            result.append(lst1[i])
        if i < lst2_len:
            result.append(lst2[i])
    return result
```