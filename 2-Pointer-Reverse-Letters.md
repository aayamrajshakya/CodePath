*[[Unit 4 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Are numbers or special characters considered as non-letters?
  - Yes, only alphabetic characters should be reversed. Numbers, punctuation, and other special characters should remain in their original positions.
- What if the string is empty or contains only non-letter characters?
  - The function should handle these cases gracefully, returning the original string unchanged if necessary.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use two pointers to identify letters from both ends of the string and swap them until they meet in the middle.

```markdown
1) Define a helper function `is_letter` to determine if a character is an alphabetic letter.
2) Convert the string into a list of characters to facilitate in-place swaps.
3) Initialize two pointers, `left` at the beginning and `right` at the end of the list.
4) While the `left` pointer is less than the `right` pointer:
  a) Move the `left` pointer rightward until it points to a letter.
  b) Move the `right` pointer leftward until it points to a letter.
  c) If both pointers point to letters, swap them and then move both pointers towards the center.
5) Convert the list back to a string and return it.
```

**⚠️ Common Mistakes**

- Ignoring non-letter characters can result in an incorrect string structure.
- Incorrectly handling the pointers could lead to swaps of non-letter characters or missing letter reversals.

## I-mplement

```python
# Helper function to check if a character is an English letter
def is_letter(c):
    return c.isalpha()

def reverse_only_letters(s):
    # Convert the string into a list of characters for easy manipulation
    chars = list(s)
    left, right = 0, len(chars) - 1

    while left < right:
        if not is_letter(chars[left]):
            left += 1
        elif not is_letter(chars[right]):
            right -= 1
        else:
            # Swap the characters
            chars[left], chars[right] = chars[right], chars[left]
            left += 1
            right -= 1

    # Convert the list of characters back to a string
    return ''.join(chars)
```