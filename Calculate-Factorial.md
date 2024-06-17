*[[Unit 1 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Will `n` always be a positive integer?
  - Yes.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Create a function that calculates the factorial of a positive integer `n`.

```markdown
1) Create and initialize a variable to store the result
2) For each number from 1 to n, multiply the result by that number
3) Return the result variable
```

**⚠️ Common Mistakes**

- Make sure your result variable is correctly initialized!  What is the smallest possible result for our factorial function?

## I-mplement

```python
def factorial(n):
	result = 1
	for num in range(1, n + 1):
		result *= num
	return result
	
```