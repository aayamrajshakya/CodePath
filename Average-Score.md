*[[Unit 1 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Should my function return an integer?
  - Not necessarily.  Some averages might happen to be integers, but you should not be rounding the results in any way.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Calculate the average of a list of integer scores.

```markdown
0) Remember that average can be calculated using (sum of values / number of values)
1) Create a variable to store the sum
2) Loop through the list, and add each value to the sum variable
3) Divide the sum variable by the length of the list and return the result
```

## I-mplement

```python
def average(scores):
	total = 0

	for score in scores:
		total += scores
	return total / len(scores)
```