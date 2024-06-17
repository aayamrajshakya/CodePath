*[[Unit 1 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Can the list be empty?
  - Yes.  If the list is empty, nothing should print.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Loop through a list, and if the index is odd, print out that element.

**⚠️ Common Mistakes**

- A number is odd when it is NOT evenly divisible by two.  How can we check that in python?

## I-mplement

```python
def print_indices(lst):
	for index in range(len(lst)):
		if index % 2 == 1:
			print(lst[index])
```

- Q: *What if I used a counter variable?* 
- A: *While this solution will also work, the extra variable takes up unnecessary space in memory.  Using `range(len(LIST))` is the more efficient way to solve the problem in Python.*
