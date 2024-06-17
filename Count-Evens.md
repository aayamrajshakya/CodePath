*[[Unit 1 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Are all elements in the list positive integers?
  - Yes.
- Can the list be empty?
  - Yes.  In that case, your function should return zero.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Create a function that counts how many even numbers are in a list of integers.

```markdown
1) Create a count variable with an initial count of zero
2) For each element in the list
  a) Check if the number is even
  b) If so, increment the count by 1
3) Return the count
```

**⚠️ Common Mistakes**

- A number is even when it is evenly divisible by two.  How can we check that in python?

## I-mplement

```python
def count_evens(lst):
	count = 0
	for num in lst:
		if num % 2 == 0:
			count += 1
	return count
```