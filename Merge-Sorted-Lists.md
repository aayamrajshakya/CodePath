*[[Unit 4 Session 2]] (Click for link to problem statements)*

## U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What happens if one of the lists is empty?
  - If one list is empty, the function should simply return the other list as it is already sorted.
- How should the function handle lists of different sizes?
  - The function should continue to merge until it has exhausted one list and then append the remainder of the other list.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Utilize two pointers to track positions in the two sorted input lists, comparing and appending the smaller current elements to the result list until one list is exhausted.

```markdown
1) Initialize an empty list called `result` for the merged output.
2) Use two pointers, `l1_index` and `l2_index`, to track positions in `lst1` and `lst2` respectively.
3) While both pointers are within the bounds of their lists:
  a) Compare the elements at the pointers.
  b) Append the smaller element to `result` and move the corresponding pointer.
4) Once one list is exhausted, append the remaining elements of the other list to `result`.
5) Return the merged list.
```

**⚠️ Common Mistakes**

- Not handling the case where the remaining elements after the main loop are not appended.
- Incorrect comparison logic leading to unsorted results.

## I-mplement

```python
def merge_sorted_lists(lst1, lst2):
    result = []
    l1_index = 0
    l2_index = 0
    
    while l1_index < len(lst1) and l2_index < len(lst2):
        if lst1[l1_index] < lst2[l2_index]:
            result.append(lst1[l1_index])
            l1_index += 1
        else:
            result.append(lst2[l2_index])
            l2_index += 1
            
    while l1_index < len(lst1):
	    result.append(lst1[l1_index])
	    l1_index += 1
	  
	  while l2_index < len(lst2):
	    result.append(lst2[l2_index])
	    l2_index += 1
	    
    return result
```