*[[Unit 1 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Will the list always contain only numbers?
  - Yes.
- Can the list be empty?
  - Yes.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Loop through a list, and generate a new list containing each element + 1.

```markdown
1) Create a function with parameters for the list
2) Make an empty list to store the results
3) Loop through the input list
  a) For each element, add the element + 1 to the results list
4) Return the results list
```

## I-mplement

```python
def increment_values(lst):
	incremented = []
	for num in lst:
		incremented.append(num + 1)
	return incremented
```