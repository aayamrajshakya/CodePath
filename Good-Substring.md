*[[Unit 4 Session 2]] (Click for link to problem statements)*

## U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- How should the function handle very short strings, like those of length less than 3?
  - The function should return 0 as there are no substrings of length three to consider.
- Are there any performance considerations?
  - For very long strings, this implementation should remain efficient since it simply iterates through the string once, checking a fixed window size of three.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Iterate through the string using a fixed-size window of three characters. At each position, check if all characters in the window are unique.

```markdown
1) Initialize a counter for good substrings to 0.
2) Loop through the string until there are less than three characters left to form a substring.
3) For each position, extract a substring of three characters.
4) Convert the substring into a set to remove duplicates and check its length.
5) If the length of the set is 3, increment the counter for good substrings.
6) Return the total count of good substrings found.
```

**⚠️ Common Mistakes**

- Misunderstanding the size of the window or not correctly adjusting the loop to stop where only complete windows can be formed.
- Incorrectly identifying unique characters by not using a set or similar structure to filter duplicates.

## I-mplement

```python
def count_good_substrings(s):
    # Initialize the count of good substrings
    count = 0
    # Loop through the string, stopping when less than 3 characters remain
    for i in range(len(s) - 2):
        # Extract the current window of size 3
        window = s[i:i+3]
        # Check if all characters in the window are unique
        if len(window) == len(set(window)):
            count += 1
    return count
```