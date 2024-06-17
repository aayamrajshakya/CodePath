*[[Unit 1 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Will the list only contain numbers?
  - Yes.
- Is there always a negative number in the list?
  - No.  If there are no negative numbers, the function should not print anything.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Create a function that prints all negative numbers in the list.

```markdown
1) Loop through each number in the list
2) If the current number is less than zero, print it out
```

## I-mplement

```python
def print_negatives(lst):
	for number in lst:
		if number < 0:
			print(number)
	
print_negatives([1,-2, 4, 3, -5]) 
# Output: 
# -2 
# -5

print_negatives([1,2,3,4,5]) 
# No output
```