*[[Unit 1 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Will `exponent` always be positive?
  - Yes, you can assume both `base` and `exponent` are positive integers.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Create a function that takes parameters `base` and `exponent` and uses repeated multiplication to calculate the exponent.

```markdown
1) Create a variable to store the total exponent
2) By default, set the total exponent to be the same as `base`
2) Loop `exponent` times, and each time multiply the total by the base
3) Return the total variable
```

## I-mplement

```python
def power(base, exponent):
	total = base
	for i in range(1, exponent + 1):
		total = total * base
	return total
```