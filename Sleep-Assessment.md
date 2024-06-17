*[[Unit 1 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Will the input always be an integer?
  - Yes.
- Should the function print anything out?
  - Yes.
  
## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Print out a result based on how many hours the user slept.

```markdown
1) Create a new function with a parameter representing the hours slept
2) Check if the number of hours meets each category.  If it does, print that result.
```

## I-mplement

```python
def sleep_assessment(hours):
	if hours < 8:
		print("Oof, go back to bed!")
	elif hours >= 8 and hours <= 10:
		print("You got a good night's rest!")
	else:
		print("You're a sleep prodigy!")
```