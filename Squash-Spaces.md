*[[Unit 4 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- How should the function deal with spaces between words?
  - The function should reduce consecutive spaces between words to a single space.
- What should happen to leading or trailing spaces?
  - Leading spaces should be ignored, and trailing spaces should not appear in the output.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use a 'left' pointer to write characters to the string and a 'right' pointer to read characters from the original string. Manage spaces carefully to ensure no leading or excessive spaces are included.

```markdown
1) Convert the input string into a list of characters to facilitate in-place modifications.
2) Initialize a 'left' pointer for writing to the list and a 'right' pointer for reading from it.
3) Use a flag `was_space` to track if the last character processed was a space, preventing consecutive spaces.
4) Iterate through the string with the 'right' pointer:
  a) If the current character is not a space, copy it to the 'left' pointer's position, increment 'left', and set `was_space` to False.
  b) If the current character is a space and `was_space` is False:
     i) Only add a space at 'left' if it's not at the start (to avoid leading spaces).
    ii) Set `was_space` to True and increment 'left' as necessary.
5) The final value of 'left' indicates where non-space characters stop; any trailing spaces are ignored.
6) Convert the modified list back to a string up to the last valid character position and return.
```

**⚠️ Common Mistakes**

- Incorrectly handling multiple consecutive spaces by either including all or removing all spaces.
- Including leading or trailing spaces due to mismanagement of the space condition checks.

## I-mplement

```python
def squash_spaces(s):
    chars = list(s)  # Convert string to list for in-place modification
    left = 0  # Initialize 'left' pointer for writing characters
    was_space = False  # Flag to track if the previous character was a space
    
    for right in range(len(chars)):  # Iterate through the string with 'right' pointer
        if chars[right] != ' ':
            chars[left] = chars[right]
            left += 1
            was_space = False
        elif not was_space:
            if left != 0:  # Avoid leading spaces
                chars[left] = ' '
                left += 1
            was_space = True
    
    return ''.join(chars[:left])
```