*[[Unit 1 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Should the function print anything?
  - No. Only return the final sum.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Create a function to return the sum of the numbers 1 to 10.

```markdown
1) Create a variable to store the total sum
2) Loop through the numbers 1 to 10, and add each to the sum variable
3) Return the sum variable
```

**⚠️ Common Mistakes**

- We could just write something like `1+2+3+4+5+6+7+8+9+10`... why might that be a bad idea?

## I-mplement

```python
def sum_ten():
	total = 0
	for i in range(1, 11):
		total += i
	return total

output = sum_ten() # Output: 55
```