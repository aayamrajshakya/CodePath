*[[Unit 3 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What if there are only repeated characters?
  - In this case, return -1.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use a dictionary to track character occurrences.

```markdown
1) First, create a dictionary to track character occurrences
2) Loop through each character of the input string
  a) Add the character to the dictionary with one occurrence if it's new
  b) Add one to the occurrence of the character in the dictionary
3) Loop through each character of the input string again, but also track the current index
  a) If that character occurs once, return the current index
4) If no character with value 1 is found in the dictionary, return -1
```

## I-mplement

```python
def first_uniq_char(myStr):
    # Count occurrences
    char_count = {}
    for char in myStr:
        if char in char_count:
            char_count[char] += 1
        else:
            char_count[char] = 1

    # Find the first non-repeating character
    for index, char in enumerate(myStr):
        if char_count[char] == 1:
            return index
    return -1
```