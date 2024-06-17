*[[Unit 3 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What if n is larger than the length of the string?
  - This won't be the case, since 0 < n < len(s).

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Slice the input string into two components and then combine them at the end.

```markdown
1) Slice the string from the beginning up to the index n
2) Slice the string from the index after n to the end
3) Return these two components added together in the order: first, last
```

## I-mplement

```python
def remove_char(s, n):
    # Create a new string 'first_part' that includes all characters from the beginning of 's' up to the character at index 'n' (not 
    inclusive).
    first_part = s[:n]

    # Create a new string 'last_part' that includes all characters from the character at index 'n+1' to the end of 's'.
    last_part = s[n+1:]

    # Return the result by concatenating 'first_part' and 'last_part', effectively removing the character at index 'n'.
    return first_part + last_part
```