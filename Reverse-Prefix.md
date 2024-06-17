*[[Unit 4 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What should happen if the character `ch` does not exist in the string `word`?
  - The function should return the original string unchanged.
- Does the function need to handle cases where `ch` appears multiple times?
  - The function only considers the first occurrence of `ch`.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Locate the first occurrence of `ch`, then reverse the segment from the start of the string to this index.

```markdown
1) Convert the string into a list to enable easy manipulation of characters.
2) Check if `ch` is in the string. If not, return the original string.
3) Find the index of the first occurrence of `ch` and store it as `right`.
4) Initialize a pointer `left` at the start of the string.
5) Use a two-pointer technique to reverse the substring from `left` to `right`:
  a) Swap the characters at `left` and `right`.
  b) Increment `left` and decrement `right` until they meet or cross.
6) Convert the list of characters back to a string and return it.
```

**⚠️ Common Mistakes**

- Not returning the original string when `ch` is not found.
- Incorrectly handling the indices or the two-pointer swap, leading to partial reversals or errors.

## I-mplement

```python
def reverse_prefix(word, ch):
    # Convert the string to a list to modify its characters
    chars = list(word)
    
    # Find the index of the first occurrence of ch
    if ch in chars:
	    right = chars.index(ch)
	  else:
		  right = -1 
    
    # If ch is not found, return the original string
    if right == -1:
        return word
    
    # Initialize the left pointer
    left = 0
    
    # Reverse the substring using the two-pointer approach
    while left < right:
        # Swap the characters at the left and right pointers
        chars[left], chars[right] = chars[right], chars[left]
        left += 1
        right -= 1
    
    # Convert the list back to a string and return it
    return ''.join(chars)
```