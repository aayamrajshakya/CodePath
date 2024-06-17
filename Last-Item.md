*[[Unit 1 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Do I need to modify the provided function?
  - No.
  
## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Create a function to safely get the last element of a list.


```markdown
1) Create a new function with a parameter for the list
2) If the list is not empty, look for the last element:
  a) Find the length of the list
  b) Get the element at index length - 1 
3) Otherwise, return None
```

**⚠️ Common Mistakes**

- Why would we look at index "length - 1" instead of just "length"?

## I-mplement

```python
# Could also do with looping and a temp variable instead of using len

def get_last(lst):
	if lst:
		length = len(lst)
		return lst[length - 1]
	else:
		return None
```