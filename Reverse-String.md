*[[Unit 3 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Will the input string ever be empty?
  - Yes, your code should allow for this.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Slice the entire string in reverse order.

```markdown
1) Return a slicing of the entire input string, but with a negated step parameter
```

## I-mplement

```python
def reverse_string(myStr):
	return myStr[::-1]

# OR

def reverse_string(myStr):
	reversed_str = ''
	for char in myStr:
		reversed_str = char + reversed_str
	return reversed_str
```