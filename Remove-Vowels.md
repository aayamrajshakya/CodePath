*[[Unit 3 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Will the string only contain letters?
  - Not necessarily!  Any characters that aren't letters should stay unchanged.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Create a new string character-by-character, skipping any characters matching a string of possible vowels.

```markdown
1) Create a string of all possible vowels
2) Create an empty string for the result
3) For each character in the input string:
  a) If the character is not in vowels string, add to result
4) Return result
```

**⚠️ Common Mistakes**

- You may be tempted to write 10 if-statements to check for each possible vowel -- but the `in` operator in python makes it much easier!

## I-mplement

```python
def remove_vowels(s):
    # Define the vowels to remove
    vowels = "aeiouAEIOU"
    # Initialize an empty string to build the result
    result = ""
    # Iterate through each character in the input string
    for char in s:
        # If the character is not a vowel, add it to the result string
        if char not in vowels:
            result += char
    # Return the result string
    return result

```