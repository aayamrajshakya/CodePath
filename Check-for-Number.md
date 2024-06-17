*[[Unit 1 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Will the list always contain only numbers?
  - Yes.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Loop through a list of numbers and check each one to see if it matches the target num.

```markdown
1) Loop through the input list
  a) If the element matches the num, return true
2) Return the counter
```

## I-mplement


```python
def check_num(lst, num):
	for item in lst:
		if item == num:
			return True
	return False
```