*[[Unit 4 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Are we considering both uppercase and lowercase vowels?
  - Yes, both cases should be considered.
- Does the order of consonants need to remain unchanged?
  - Yes, only the vowels should be moved.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Identify vowels using a helper function, then use two pointers to swap the vowels from both ends towards the middle.

```markdown
1) Define a helper function `is_vowel` to check if a character is a vowel.
2) Convert the string to a list for in-place modifications.
3) Initialize two pointers, `left` at the beginning and `right` at the end of the list.
4) While `left` pointer is less than `right` pointer:
  a) Increment `left` until it points to a vowel.
  b) Decrement `right` until it points to a vowel.
  c) Swap the characters at `left` and `right`.
  d) Move both `left` and `right` inward to continue the process.
5) Convert the list back to a string and return.
```

**⚠️ Common Mistakes**

- Skipping characters that are vowels due to incorrect condition checks.
- Incorrect handling of the two pointers can cause an infinite loop or early termination of the function.

## I-mplement

```python
def is_vowel(c):
    # Check if a character is a vowel (considering both lowercase and uppercase)
    return c in 'aeiouAEIOU'

def reverse_vowels(s):
    # Convert the string to a list to modify it in place
    s_list = list(s)
    left = 0
    right = 0 len(s) - 1

    while left < right:
        # Move the left pointer until it points to a vowel
        while left < right and not is_vowel(s_list[left]):
            left += 1
        # Move the right pointer until it points to a vowel
        while left < right and not is_vowel(s_list[right]):
            right -= 1
        # Swap the vowels
        temp = s_list[left]
        s_list[left] = s_list[right]
        s_list[right] = temp
        left = left + 1
        right = right - 1

    # Convert the list back into a string
    return ''.join(s_list)
```