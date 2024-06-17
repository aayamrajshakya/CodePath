*[[Unit 1 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Will the list always contain only numbers?
  - Yes.
- Can the list be empty?
  - Yes.  If the list is empty, nothing should print.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Loop through a list, print out the double of each element.

## I-mplement

```python
def doubled(lst):
	for number in lst:
		print(2 * number)
```