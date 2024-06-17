*[[Unit 1 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Will the input always be an integer?
  - Yes.
- Should the function print anything out?
  - No, it should return the answer as a string.
  
## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Return "adult" if the provided number is over 18, and "child" otherwise.

```markdown
1) Set up the function:
  a) Create a new function with a parameter representing age
  b) If the age is less than 18, return the string "child"
  c) Otherwise, return the string "adult"
2) Test the function for values over, under, and equal to 18 by:
  a) Calling the function and saving the result to a variable
  b) Printing out the result.
```

**⚠️ Common Mistakes**

- Make sure your code handles someone who is exactly 18 correctly!

## I-mplement

```python
def classify_age(age):
	if age < 18:
		return "child"
	else: 
		return "adult"

output = classify_age(18)
print(output)
output = classify_age(7)
print(output)
output = classify_age(50)
print(output)
```