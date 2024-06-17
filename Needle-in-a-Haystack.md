*[[Unit 3 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What if the needle is not in the haystack?
  - In this case, return -1.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Loop through the indices of haystack and compare needle-sized strings to needle.

```markdown
1) If needle is an empty string, return 0
2) Loop through the length of haystack minus the length of needle plus 1 (so it is inclusive)
  a) If the string sliced from the current index to the index that would put us at the end of the string needle (so it is the same size) is 
     equal to needle, return the current index
3) If the loop ends without returning, return -1 since the needle was not found
```

## I-mplement

```python
def find_the_needle(haystack, needle):
    if not needle:
        return 0
    needle_length = len(needle)
    for i in range(len(haystack) - needle_length + 1):
        if haystack[i:i+needle_length] == needle:
            return i
    return -1
```