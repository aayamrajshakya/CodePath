*[[Unit 4 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What happens if the `typed` string is shorter than the `name` string?
  - It should return `False`, as not all characters from `name` can be accounted for.
- What if there are extra characters at the end of `typed` that do not match the last character of `name`?
  - The function should return `False` as it indicates a mismatch in the sequence.


## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use a two-pointer technique to match characters from `name` to `typed`. If characters match, move both pointers. If they don't, but the character repeats in `typed`, move only the `typed` pointer.

```markdown
1) Start with two pointers, i and j, at the beginning of `name` and `typed` respectively.
2) Loop through both strings while both pointers are within the bounds of their respective strings.
  a) If characters at both pointers match, move both pointers.
  b) If they don't match but current `typed` character is the same as the previous one, move `typed` pointer.
  c) Otherwise, return False because of a mismatch.
3) After the loop, ensure all characters in `name` are accounted for.
4) Also ensure any extra characters in `typed` match the last character in `name`.
5) If both conditions are satisfied, return True, otherwise False.
```

**⚠️ Common Mistakes**

- Not checking for the end of the `name` while `typed` might still have valid repeated characters.
- Failing to verify the remaining characters in `typed` after the main loop.

## I-mplement

```python
def is_long_pressed(name, typed):
    i, j = 0, 0  # Initialize two pointers for name and typed strings
    
    while i < len(name) and j < len(typed):
        if name[i] == typed[j]:
            i += 1
            j += 1
        elif j > 0 and typed[j] == typed[j-1]:
            j += 1
        else:
            return False
    
    # If there are still characters left in name, it means not all characters were matched
    if i < len(name):
        return False
    
    # Check remaining characters in typed to ensure they are all the same as the last character in name
    while j < len(typed):
        if typed[j] != name[-1]:
            return False
        j += 1
    
    return True
```