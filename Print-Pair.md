*[[Unit 2 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Print a requested dictionary entry, or an error if not found.

```markdown
1) Check if the target is in the dictionary keys
2) If so:
  a) print the target as the key
  b) use the key to get the value and print the value
3) If not, print an error message
```

## I-mplement

```python
def print_pair(dictionary, target):
	if target in dictionary:
		print("Key: " + target)
		print("Value: " + dictionary[target])
	else:
		print("That pair does not exist!")
``` 