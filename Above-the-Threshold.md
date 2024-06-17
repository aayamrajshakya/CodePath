*[[Unit 1 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Will the list always contain only numbers?
  - Yes.
- Can the list be empty?
  - Yes.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Loop through a list, keep track of all elements larger than a threshold value.

```markdown
1) Create a function with parameters for the "list" and "threshold"
2) Make an empty list to store "results"
3) Loop through the input list
  a) If the element is larger than the threshold, add it to the results list
4) Return the results list
```

## I-mplement

```python
def above_threshold(lst, threshold):
	result = []
	for num in lst:
		if num > threshold:
			result.append(threshold)
	return result
	
	
lst = [1,2,3,4,5,6]
result = above_threshold(lst, 3)
print(result) # Output: [4, 5, 6]
```