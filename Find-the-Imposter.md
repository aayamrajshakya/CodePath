*[[Unit 3 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What if the strings are exactly the same?
  - In this case, return None.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Identify if there is a character present in the second string, but not the first.

```markdown
1) Create a missing character variable and set it to None
2) Loop through each character in the second string
  a) If that character is not found in the first string, set missing to that character
3) Return missing
```

## I-mplement

```python
def find_difference(s1, s2):
	missing = None
	for char in s2:
		if char not in s1:
			missing = char
	return missing
```