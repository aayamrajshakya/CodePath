*[[Unit 1 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Will `stop` always be a positive integer?
  - Yes.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Create a function that takes a parameter `stop` and returns the sum of the numbers 1 to `stop`.

```markdown
1) Create a variable to store the total sum
2) Loop through the numbers 1 to "stop", and add each to the sum variable
3) Return the sum variable
```

**⚠️ Common Mistakes**

- Make sure your loop includes the final number!

## I-mplement

```python
def sum_positive_range(stop):
	total = 0
	for num in range(1, stop + 1):
		total += num
	return total
```