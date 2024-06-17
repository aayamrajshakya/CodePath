*[[Unit 3 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What will the function output?
  - It should return the reversed string.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Make a list of all letters in the string, then build a new string that reverses only the letters.

```markdown
1) Create an empty list for the letters
2) Loop through the string, and add any letters to the list
3) Make an index variable, set to end of letters list
4) Create an empty results string
5) Loop through each character in the original string
  a) If the char was a letter:
     i) add the value at letters[index] to results
    ii) reduce index by 1
  b) Otherwise, add the char itself to results
6) Return results
```

## I-mplement

```python
def reverse_only_letters(s):
    letters = []  # Collect letters 
    for c in s:
        if c.isalpha():
            letters.append(c)
    
    result = ""
    letters_index = len(letters) - 1  # Start from the end of the letters list
    
    for c in s:
        if c.isalpha():
            result += letters[letters_index]
            letters_index -= 1
        else:
            result += c
    return result

```