*[[Unit 3 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Will the string contain only numeric characters?
  - Yes, it will consists of digits 0-9.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** For each character in the string, convert to integer and add to an output list.

```markdown
1) Create an empty result list
2) For each character
  a) Convert that character to an int
  b) Add that int to the result list
3) Return the result list
```

**⚠️ Common Mistakes**

- You don't need to write complicated code to convert digit characters to ints -- instead, you can use a built-in python function to do it in one line.

## I-mplement

```python
def string_to_integer_mapping(s):
    # Initialize an empty list to hold the integer values
    result = []
    # Iterate through each character in the string
    for char in s:
        # Convert the character to an integer and append it to the result list
        result.append(int(char))
    # Return the result list
    return result
```