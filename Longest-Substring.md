*[[Unit 3 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What if there are only repeated characters?
  - In this case, the longest substring would end up being 0.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Loop through the input string, tracking the longest streak of no repeating characters.

```markdown
1) First, set two counters: a start index and substring maxLength, and a dictionary usedChar
2) Loop through each character of the input string while tracking the current index
  a) If the character is in usedChar and start is less than or equal to the index of the previous character occurrence
    i) Set start to be one more than the index of the previous character
  b) Otherwise, set maxLength to be the higher of the current maxLength and one more than the difference between the current index and start
  c) Also, record the current index with the current character in usedChar
3) Return maxLength
```

## I-mplement

```python
def length_of_longest_substring(s):
    start = maxLength = 0
    usedChar = {}
    
    for i, char in enumerate(s):
        if char in usedChar and start <= usedChar[char]:
            start = usedChar[char] + 1
        else:
            maxLength = max(maxLength, i - start + 1)
        usedChar[char] = i
    
    return maxLength
```