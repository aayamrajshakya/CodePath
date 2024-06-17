*[[Unit 4 Session 2]] (Click for link to problem statements)*

## U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What happens if k is greater than the length of the string `s`?
  - If k is greater than the length of `s`, the function should return the count of vowels in `s` since no sub-string of length k can be formed.
- How does the function handle strings with no vowels?
  - If there are no vowels in the string, the function should return 0, indicating no vowels were found in any substring.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use the sliding window technique to count the number of vowels in every substring of length k, tracking the maximum count found.

```markdown
1) Define a helper function `is_vowel(c)` to check if a character is a vowel.
2) Initialize `max_vowels` to track the maximum number of vowels found in any window, and `current_vowels` for the number in the current window.
3) Iterate through the first `k` characters of `s` to set up the initial window:
  a) If a character is a vowel, increment `current_vowels`.
4) Assign the count from the initial window to `max_vowels`.
5) Continue the sliding window across `s` starting from the `k`th character:
  a) For the new character entering the window, if it's a vowel, increment `current_vowels`.
  b) For the character leaving the window, if it's a vowel, decrement `current_vowels`.
  c) Update `max_vowels` with the higher value between `max_vowels` and `current_vowels`.
6) Return the value of `max_vowels`.
```

**⚠️ Common Mistakes**

- Not initializing `max_vowels` correctly after the initial window is set up.
- Forgetting to update `current_vowels` when the window slides (both incrementing and decrementing).

## I-mplement

```python
def is_vowel(c):
    # Check if the character is a vowel
    return c in 'aeiou'

def max_vowels(s, k):
    max_vowels, current_vowels = 0, 0
    
    # Initialize the first window and count the vowels in it
    for i in range(k):
        if is_vowel(s[i]):
            current_vowels += 1
    max_vowels = current_vowels
    
    # Slide the window across the string
    for i in range(k, len(s)):
        # If the new character is a vowel, increment current_vowels
        if is_vowel(s[i]):
            current_vowels += 1
        # If the character that's leaving the window is a vowel, decrement current_vowels
        if is_vowel(s[i - k]):
            current_vowels -= 1
        # Update max_vowels if necessary
        max_vowels = max(max_vowels, current_vowels)
        
    return max_vowels

```