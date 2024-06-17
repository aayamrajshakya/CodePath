*[[Unit 4 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What types of efficiency should we be comparing based on?
  - We evaluate both the time and space complexity.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**Two-pointer method:**
```markdown
- **Time Complexity:** O(n), where `n` is the length of the string. Each comparison reduces the problem size by 2 until the middle is reached.
- **Space Complexity:** O(1) since we are only using two pointers and no additional data structures.
```

**Reverse string method:**
```markdown
- **Time Complexity:** O(n), similar to the two-pointer method, as reversing the string also traverses all characters.
- **Space Complexity:** O(n), due to the storage required for the reversed string.
```

## I-mplement

```python
# NON TWO POINTER
# Time complexity: O(n)
# Space complexity: O(n)
def is_palindrome(s):
    reverse = s[::-1] # O(n) space and time: https://www.geeksforgeeks.org/python-reversing-list/
    return reverse == s
        
# TWO POINTER
# Time complexity: O(n)
# Space complexity: O(1)
def is_palindrome(s):
    left = 0
    right = len(s) - 1 # O(1) time/space(Getting length of list is an O(1) operation in python: https://www.geeksforgeeks.org/complexity-cheat-sheet-for-python-operations/)
    while left < right: # O(n/2) --> O(n) time 
        if s[left] != s[right]:
            return False
        left += 1
        right -= 1
    return True
```

**Takeaway**
- For space-sensitive situations, the two-pointer solution is often preferable due to its O(1) space complexity, despite both methods having the same time complexity.