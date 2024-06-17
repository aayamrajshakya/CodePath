*[[Unit 1 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Will the list always contain only numbers?
  - Yes.
- Can the list be empty?
  - No.  The list will have at least one value.
  - In the case of only one value, your function should return "0".

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Loop through a list of numbers, and calculate the maximum difference between any two entries.

```markdown
1) Create a variable to store the current maximum
2) Create a variable to store the current minimum
3) Set both current max and current min to first element in list
4) Loop through the input list
  a) If the value is larger than max, set max to the new value
  b) If the value is less than min, set min to the new value
5) When the loop is done, we should have the true min and max of the list
6) Subtract the min from the max and return the result
```

## I-mplement

```python
def max_difference(lst):
	max_val = lst[0]
	min_val = lst[0]
	
	for num in lst:
		if num > max_val:
			max_val = num
		if num < min_val:
			min_val = num
	
	return max_val - min_val
```