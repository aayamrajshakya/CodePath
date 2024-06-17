*[[Unit 1 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Will the input always be an integer?
  - Yes.
- Should the function print anything out?
  - No, it should return the answer as a string.
  
## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Print out what time it is based on the current hour

```markdown
1) Set up the function:
  a) Create a new function with a parameter representing the hour
  b) Check for each time, and if it matches, return the appropriate string
2) Test the function for all possible results by:
  a) Calling the function and saving the result to a variable
  b) Printing out the result.
```

## I-mplement

```python
def what_time_is_it(hour):
	if hour == 2:
		return "taco time"
	elif hour == 12:
		return "peanut butter jelly time"
	else:
		return "nap time"

time = what_time_is_it(2)
print(time)
time = what_time_is_it(12)
print(time)
time = what_time_is_it(7)
print(time)
```