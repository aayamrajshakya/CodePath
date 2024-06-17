*[[Unit 1 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Are all elements in the list positive integers?
  - Yes.
- Can the list be empty?
  - Yes.  In that case, your function should return zero.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Create a function that takes in a list and returns a sub-list containing only the even numbers.

```markdown
1) Create an empty list to store the result
2) For each element in the list
  a) Check if the number is even
  b) If so, add the number to the result list
3) Return the result list
```

**⚠️ Common Mistakes**

- A number is even when it is evenly divisible by two.  How can we check that in python?

## I-mplement

```python
def get_evens(lst):
	evens = []
	for num in lst:
		if num % 2 == 0:
			evens.append(lst)
	return evens
```