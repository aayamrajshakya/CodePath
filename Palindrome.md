*[[Unit 4 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- How does the function handle an empty list?
  - It returns an empty string as there are no strings to check.
- What is the case sensitivity for checking palindromes?
  - Assume palindromes ARE case-sensitive (e.g., "raceCAR" is not a palindrome).

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Check each string in the list to see if it is a palindrome using a helper function.

```markdown
1) Define a helper function is_palindrome(s):
  a) Initialize two pointers, left starting at the beginning of the string, and right at the end.
  b) Loop while left is less than right:
      i) If characters at left and right are not the same, return False (not a palindrome).
     ii) Move left pointer one step to the right.
    iii) Move right pointer one step to the left.
  c) If no mismatches are found, return True (it is a palindrome).

2) Define the main function first_palindrome(words):
  a) Loop through each word in the list:
     i) Use the is_palindrome function to check if the current word is a palindrome.
    ii) If a palindrome is found, return that word immediately.
  b) If no palindromes are found after checking all words, return an empty string.
```

**⚠️ Common Mistakes**

- Not considering edge cases like an empty list or single character strings, which are inherently palindromic.
- Incorrectly moving the pointers in the palindrome check can result in false negatives.

## I-mplement

```python
def is_palindrome(s):
    left, right = 0, len(s) - 1
    while left < right:
        if s[left] != s[right]:
            return False
        left += 1
        right -= 1
    return True

def first_palindrome(words):
    for word in words:
        if is_palindrome(word):
            return word
    return ""
```