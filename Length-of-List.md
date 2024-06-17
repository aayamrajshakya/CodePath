*[[Unit 1 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Will the list ever be empty?
  - Yes, it might be empty.  Be sure your code can handle that.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Create a function that takes parameters in a list and returns the length of the list, without using `len()`.

```markdown
1) Create a count variable, initialized to zero
2) Loop through each element in the list
  a) Add 1 to the count each time
3) Return the count variable
```

## I-mplement

```python
def list_length(lst):
	count = 0
	for item in lst:
		count += 1
	return count
```