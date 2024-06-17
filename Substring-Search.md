*[[Unit 7 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 15 mins
* 🛠️ **Topics**: Recursion, String Manipulation
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: What should the function do if the substring is longer than the main string?
  - A: If the substring is longer than the main string, the function should return 0, as no occurrences can exist.

```
HAPPY CASE
Input: s = "ababc", sub = "ab"
Output: 2
Explanation: The substring "ab" occurs twice in "ababc" - at the start and at index 2.

EDGE CASE
Input: s = "aaaaa", sub = "aa"
Output: 2
Explanation: "aa" occurs twice without overlapping in "aaaaa".
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem is an application of string manipulation and recursion:

- Using recursion to navigate through the string and count occurrences of a specified substring.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use recursion to count how many times a substring occurs in a string by checking from the start and then moving the starting point.

```markdown
1) Base Case: If the main string length is less than the substring length, return 0.
2) Recursive Case:
   - Check if the current segment of the main string starting from index 0 equals the substring.
   - If it matches, increment the count and move the starting index by the length of the substring.
   - If not, only move the starting index by one.
3) Return the count.
```

**⚠️ Common Mistakes**

- Not handling overlaps correctly could lead to incorrect counts.
- Forgetting to adjust the index properly during recursion which might cause infinite loops or missed counts.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def count_substring(s, sub):
    sub_len = len(sub)
    
    # Base case: If the remaining string is shorter than the substring
    if len(s) < sub_len:
        return 0
    
    # Check if the current position contains the substring
    if s[:sub_len] == sub:
        # Skip the length of the substring to avoid overlap
        return 1 + count_substring(s[sub_len:], sub)
    else:
        # Move one character forward
        return count_substring(s[1:], sub)
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Test the function with "ababc" and sub = "ab" to ensure it returns 2.
- Validate with "aaaaa" and sub = "aa" to confirm the count is 2, considering non-overlapping occurrences.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: The worst-case complexity is `O(n*m)` where `n` is the length of the string `s` and `m` is the length of the substring `sub`, especially when no matches are found early in the string.
* **Space Complexity**: `O(n)` due to the recursion stack that could potentially grow with the size of the input string in the worst case.
