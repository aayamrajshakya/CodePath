*[[Unit 7 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 10 mins
* 🛠️ **Topics**: Recursion, String Manipulation
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: How should the function handle an empty string?
  - A: The function should return 0 for an empty string, indicating that it has no characters.

```
HAPPY CASE
Input: "hello"
Output: 5
Explanation: The string "hello" has 5 characters.

EDGE CASE
Input: ""
Output: 0
Explanation: An empty string has 0 characters.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem is a fundamental example of using recursion to solve simple computational problems:

- Understanding recursion as breaking down a problem into smaller pieces.
- Using recursion to iterate through a string one character at a time to count its length.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Write a recursive function to calculate the length of a string by processing one character at a time.

```markdown
1) Base Case: If the string is empty, return 0.
2) Recursive Case: Return 1 plus the recursive call for the substring starting from the second character.
```

**⚠️ Common Mistakes**

- Not correctly identifying the base case, which could lead to an infinite recursion or incorrect counting.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def string_length(s):
    if s == "":
        return 0
    else:
        return 1 + string_length(s[1:])
```
    
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with input "hello" to ensure it correctly calculates the length as 5.
- Validate the function with an empty string to confirm that it returns 0.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(n)` where `n` is the length of the string, since each recursive call processes one character.
* **Space Complexity**: `O(n)` due to the recursion stack depth, which grows linearly with the length of the string.
