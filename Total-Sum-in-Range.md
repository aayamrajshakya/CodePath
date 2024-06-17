*[[Unit 1 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Will `start` and `stop` always be positive integers?
  - Yes.
- Will `start` ever be larger than `stop`?
  - No.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Create a function that takes parameters `start` to `stop` and returns the sum of the numbers from `start` to `stop`.

```markdown
1) Create a variable to store the total sum
2) Loop through the numbers "start" to "stop", and add each to the sum variable
3) Return the sum variable
```

**⚠️ Common Mistakes**

- Make sure your loop includes the first number and the final number!

## I-mplement

```python
def sum_range(start, stop):
	total = 0
	for num in range (start, stop + 1):
		total += num
	return total
```