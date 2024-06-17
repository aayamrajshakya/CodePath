*[[Unit 4 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What if the string is empty?
  - An empty string is considered a palindrome as it reads the same forward and backward.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use two pointers to compare characters from the beginning and end of the string moving towards the center.

```markdown
1) Initialize two pointers, left at the start (0) and right at the end (length of s - 1)
2) While left pointer is less than right pointer:
  a) If characters at left and right pointers do not match, return False
  b) Increment left pointer and decrement right pointer
3) If all characters match, return True
```

**⚠️ Common Mistakes**

- Not handling strings of different lengths properly.
- Incorrectly initializing the pointers.

## I-mplement

```python
def is_palindrome(s):
    left = 0
    right = len(s) - 1
    while left < right:
        if s[left] != s[right]:
            return False
        left += 1
        right -= 1
    return True
```