*[[Unit 3 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Will the input string ever be empty?
  - Yes, we will want to account for this case.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Loop through the input string and track the count of the current character.

```markdown
1) First, account for if the string is empty
2) Otherwise, set a result string to be returned later, a count to 1, and the current_char in the string
3) Loop through the length of the string (starting at the 2nd character)
  a) If the current indexed character is the same as current_char, increase count by 1
  b) Otherwise, add current_char and its count to result, update current_char to the currently indexed character, and reset the count
4) Add the last character and its count to result
5) If result is shorter than the length of the input string, return result
6) Otherwise, return the input string
```

## I-mplement

```python
def compress_string(myStr):
    if not myStr:
        return ""
    result = ""
    count = 1
    current_char = myStr[0]
    for i in range(1, len(myStr)):
        if myStr[i] == current_char:
            count += 1
        else:
            result += current_char + str(count)
            current_char = myStr[i]
            count = 1
    result += current_char + str(count)
    if len(result) < len(myStr):
        return result
    else:
        return myStr
```