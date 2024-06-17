*[[Unit 1 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Can the list be empty?
  - Yes.  In that case, your function should return an empty list.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Create a function that squares every element in a list.

```markdown
1) Create and initialize an empty list to hold the result 
2) For each element in the list
  a) calculate the square 
  b) add the squared value to the result list
3) Return the result list
```

## I-mplement

```python
def squares(nums):
	squared = []
	for num in nums:
		squared.append(num * num)
	return squared
```