*[[Unit 3 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What if the input string is empty?
  - This case will be determined not a pangram and return False.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Check if each and every letter of the alphabet is found in the input string.

```markdown
1) First create a string of every letter in the alphabet
2) Loop over each character of the alphabet string
  a) If the character is in the input string, do nothing (keep looping)
  b) If the character is not in the input string, return False
3) If the loop ends and all characters are found, return True
```

## I-mplement

```python
def is_pangram(myStr):
    alphabet = "abcdefghijklmnopqrstuvwxyz"
    for char in alphabet:
        if char not in myStr.lower():
            return False
    return True
```