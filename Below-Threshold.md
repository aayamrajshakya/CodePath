*[[Unit 1 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Will the list always contain only numbers?
  - Yes.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Loop through a list of numbers, and count how many numbers in the list are less than a given threshold.

```markdown
1) Create a function with parameters for the list and threshold
2) Initialize a counter variable to zero
3) Loop through the input list
  a) If the element is less than the threshold, add 1 to the counter
4) Return the counter
```

## I-mplement

```python
def count_less_than(numbers, threshold):
	count = 0
	for num in numbers:
		if num < threshold:
			count += 1
	return count
```