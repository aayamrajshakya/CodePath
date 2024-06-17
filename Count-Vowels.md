*[[Unit 3 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Can the string include capital and lowercase characters?
  - Yes, we will want to account for this.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Compare each character of the input string to vowels and sum the occurrences.

```markdown
1) Set a string of vowels to compare to later
2) Set the count of vowels found to 0
3) Loop through the input string
  a) If the lowercase version of the character is in the string of vowels, add one to the count
4) Return the count of vowels
```
 
## I-mplement

```python
def vowel_count(s):
    vowels = "aeiou"
    count = 0
    for char in s:
        if char.lower() in vowels:
            count += 1
    return count
```