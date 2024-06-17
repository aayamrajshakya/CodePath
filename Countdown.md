*[[Unit 1 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Will `m` and `n` always be positive integers?
  - Yes.
- Will `n` ever be larger than `m`?
  - No.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Create a function that takes parameters `n` and `m` and counts down the numbers from `m` down to `n`.

```markdown
1) Loop through the numbers starting at `m`, ending at `n`, and stepping -1 each time
2) Print each number
```

**⚠️ Common Mistakes**

- Make sure your loop includes the first number and the final number!
- How can you tell `range()` to step -1 each time?

## I-mplement

```python
def countdown(m, n):
	for num in range (m, n-1, -1):
		print(num)
```