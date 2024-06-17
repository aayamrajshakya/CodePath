*[[Unit 4 Session 2]] (Click for link to problem statements)*

## U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What happens when one string is shorter but has more backspaces that lead to a longer effective length?
  - The comparison checks each character after accounting for backspaces, so strings that are effectively the same will return True, even if their raw forms are different.
- How does the function handle multiple consecutive backspace characters?
  - It correctly calculates the effective string by skipping characters as needed based on the count of backspaces.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use a helper function to navigate each string from the end to the beginning, accounting for backspaces and comparing the resulting characters from each string.

```markdown
1) Define a helper function that returns the index of the next valid character in the string by accounting for backspaces.
2) Initialize pointers for both strings at the end.
3) While either pointer has not reached the beginning of the string:
  a) Use the helper function to find the next valid character for both strings.
  b) Compare these characters:
     i) If they are different, return False.
     ii) If one string has characters left and the other doesn't, return False.
  c) Decrement both pointers.
4) If all comparisons are valid, return True.
```

**⚠️ Common Mistakes**

- Not properly handling cases where backspaces exceed the number of characters in front of them, potentially causing out-of-bound errors or incorrect character comparisons.
- Misaligning the decrement operations which could lead to incorrect character comparisons or skipping characters.

## I-mplement

```python
def get_next_valid_char_index(string, index):
  # Count of backspaces
  backspace_count = 0
  while index >= 0:
      if string[index] == '#':
          backspace_count += 1
      elif backspace_count > 0:
          backspace_count -= 1
      else:
          break
      index -= 1
  return index


def backspace_compare(s, t):

    i, j = len(s) - 1, len(t) - 1
    while i >= 0 or j >= 0:
        i = get_next_valid_char_index(s, i)
        j = get_next_valid_char_index(t, j)
        
        if i >= 0 and j >= 0 and s[i] != t[j]:
            return False
        if (i >= 0) != (j >= 0):
            # One is at the end, the other isn't
            return False
            
        i -= 1
        j -= 1
    
    return True
```