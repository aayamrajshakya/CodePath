*[[Unit 1 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Can the list be empty?
  - Yes.  If the list is empty, nothing should print.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Loop through a list, print out the index of each element.

## I-mplement

```python
	def print_indices(lst):
		for index in range(len(lst)):
			print(index)
```

- Q: *What if I used a counter variable?* 
- A: *While this solution will also work, the extra variable takes up unnecessary space in memory.  Using `range(len(LIST))` is the more efficient way to solve the problem in Python.*
