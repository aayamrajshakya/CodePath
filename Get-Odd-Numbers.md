*[[Unit 1 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Are all elements in the list positive integers?
  - Yes.
- Can the list be empty?
  - Yes.  In that case, your function should return an empty list.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Create a function that counts how many even numbers are in a list of integers.

```markdown
1) Create an empty list to store the results
2) For each element in the list
  a) Check if the number is odd
  b) If so, add it to the results list
3) Return the results list
```

**⚠️ Common Mistakes**

- A number is odd when it is NOT evenly divisible by two.  How can we check that in python?

## I-mplement

```python
def get_odds(lst):
	odds = []
	for num in lst:
		if num % 2 == 1:
			odds.append(lst)
	return odds
```