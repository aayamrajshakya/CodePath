*[[Unit 4 Session 2]] (Click for link to problem statements)*

## U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What happens if the input string is empty?
  - The function should return True, as an empty string or a string with a single character is trivially a palindrome.
- How does the function handle case sensitivity and non-alphanumeric characters?
  - Assuming standard palindrome conditions where only alphanumeric characters are considered and they are case insensitive. However, this specific implementation does not address these issues and treats the string as is.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use a helper function to check for palindrome by comparing characters from both ends. If a mismatch is found, check the possibility of forming a palindrome by removing one character either from the left or the right.

```markdown
1) Start with two pointers at the beginning and end of the string.
2) While the two pointers haven't met:
  a) If characters at the pointers match, move both pointers towards the center.
  b) If they don't match:
     i) Check if skipping the character at the left pointer results in a palindrome.
    ii) Check if skipping the character at the right pointer results in a palindrome.
    iii) Return True if either of the above checks returns True.
3) Return True if no mismatches were severe enough to prevent a palindrome (after considering one removal).
```

**⚠️ Common Mistakes**

- Not considering both possibilities of removing characters when a mismatch is found.
- Mismanaging pointers which could lead to incorrect comparisons or missing the chance to verify potential palindromes.


## I-mplement

```python
def is_palindrome(s, left, right):
    while left < right:
        if s[left] != s[right]:
            return False
        left, right = left + 1, right - 1
    return True

def valid_palindrome(s):
    left, right = 0, len(s) - 1
    
    while left < right:
        # When characters mismatch, check the two possibilities
        if s[left] != s[right]:
            # Check by skipping left character or skipping right character
            return is_palindrome(s, left + 1, right) or is_palindrome(s, left, right - 1)
        left, right = left + 1, right - 1
    
    # If it's already a palindrome or can be one by removing a character
    return True
```