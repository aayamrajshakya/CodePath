*[[Unit 3 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What if there are no repeated characters?
  - In this case, return None.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Loop through the input string while maintaining a tracker of previously seen characters.

```markdown
1) Create a list to track seen characters
2) Loop through the input string while also tracking current index
  a) If the character has previously been found in the string, return the current index
  b) Otherwise add the character to the list of seen characters
3) If no characters end up being seen twice, return None
```

## I-mplement

```python
def first_repeated_char(s):
    seen_chars = []
    for index, char in enumerate(s):
        if char in seen_chars:
            return index
        seen_chars.append(char)
    return None
```