*[[Unit 3 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What if the string is empty?
  - In that case, the count would be 0.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Loop through the string, keeping track of both the current consecutive count and the maximum found so far.

```markdown
1) If string is empty, return 0
2) Assume max count is 1 and current count is 1
3) For each character in the string (skipping the first)
  a) If the character matches the one before it
     i) add 1 to current
    ii) if current > max, update max 
  b) If no match, reset current to 1
4) Return max
```

## I-mplement

```python
def count_consecutive_characters(s):
    if not s:
        return 0
    max_count = 1
    current_count = 1
    for i in range(1, len(s)):
        if s[i] == s[i-1]:
            current_count += 1
            max_count = max(max_count, current_count)
        else:
            current_count = 1
    return max_count
```