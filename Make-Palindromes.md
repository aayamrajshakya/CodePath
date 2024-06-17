*[[Unit 4 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- How do we handle strings that are already palindromes?
  - No operations are needed; the function should return the string as is.
- What is the priority when choosing which character to change?
  - The goal is to create the lexicographically smallest palindrome.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use two pointers to compare and adjust characters from the start and end of the string.

```markdown
1) Convert the string into a list of characters to allow modification.
2) Initialize two pointers: left at the start and right at the end of the string.
3) While left pointer is less than right pointer:
  a) If characters at the two pointers are different:
     i) Replace the character at the higher index with the smaller character of the two.
  b) Increment the left pointer and decrement the right pointer.
4) Join the list of characters back into a string and return it.
```

**⚠️ Common Mistakes**

- Incorrectly replacing characters that could lead to a non-lexicographical order.
- Forgetting to handle the case where no changes are needed because the string is already a palindrome.

## I-mplement

```python
def make_palindrome(s):
    # Convert the string to a list to modify characters
    chars = list(s)
    left, right = 0, len(s) - 1

    while left < right:
        if chars[left] != chars[right]:
            # Replace the character at the higher index with the smaller of the two
            if chars[left] > chars[right]:
                chars[left] = chars[right]
            else:
                chars[right] = chars[left]
        left += 1
        right -= 1

    # Convert the list back to a string
    return "".join(chars)
```