*[[Unit 3 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Will the string ever be empty?
  - Yes, we should account for this case.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Loop through the input string and track the longest sequence of the same characters in a row.

```markdown
1) If the input string is empty, return 0
2) Set a variable to track the largest uniform substring and the current uniform substring
3) Loop through the length of the input string
  a) If the current and previous characters are equal, increase the current uniform substring counter and update the largest uniform 
     substring counter
  b) Otherwise, reset the current uniform substring counter to 1
4) Return the largest uniform substring counter
```

## I-mplement

```python
def longest_uniform_substring(s):
    if not s:
        return 0
    max_length = 1
    current_length = 1
    for i in range(1, len(s)):
        if s[i] == s[i-1]:
            current_length += 1
            max_length = max(max_length, current_length)
        else:
            current_length = 1
    return max_length
```