*[[Unit 1 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** First, move all non-zero elements to the beginning of the list, preserving their order.  Then fill the remaining space with zeroes.

```markdown
1) Create a new list to store the result
2) Loop through the numbers and add each non-zero number into the results list
3) Count how many zeroes were in the original list
4) Add that many zeroes to the end of the results list
```

## I-mplement

```python
def move_zeroes(nums):
	result = []
	for num in nums:
		if num != 0:
			result.append(num)
		
	zero_count = nums.count(0)
	for num in range(1, zero_count + 1):
		result.append(0)

    return result
```

Alternatively, you can deduce the number of zeroes by subtracting the length of the "non-zeroes" list from the length of the original list:

```python
def move_zeroes(nums):
	result = []
	for num in nums:
		if num != 0:
			result.append(num)
		
	zero_count = len(nums) - len(result)
	for num in range(1, zero_count + 1):
		result.append(0)

    return result
```