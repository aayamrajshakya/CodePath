*[[Unit 1 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Do I need to modify the provided function?
  - No.
  
## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Create a function to safely get the first element of a list.


```markdown
1) Create a new function with a parameter for the list
2) If the list is not empty, return the first item
3) Otherwise, return None
```

## I-mplement

```python
def get_first(lst):
	if lst:
		return lst[0]
	return None
```