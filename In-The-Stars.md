*[[Unit 7 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 10 mins
* 🛠️ **Topics**: Recursion, String Manipulation, Iteration
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: What should happen if the string is empty or has only one character?
  - A: If the string is empty or has one character, it should be returned as is without any stars.

```
HAPPY CASE
Input: "hello"
Output: "h*e*l*l*o"
Explanation: Stars are inserted between each character.

EDGE CASE
Input: "h"
Output: "h"
Explanation: No stars are added as there's only one character.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem is a string manipulation challenge that can be solved using both recursion and iteration:

- Using recursion to break down the problem and insert stars between each consecutive character.
- Using iteration to traverse through the string and construct a new string with stars.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Given a recursive implementation, write an iterative implementation, to insert '*' between each character of a given string.

```markdown
**Recursive Approach: (Provided)**
1) Base Case: If the string length is 1 or less, return the string as is.
2) Recursive Case: Return the first character + '*' + recursive call on the rest of the string.
```

```markdown
**Iterative Approach:**
1) If the string length is 1 or less, return the string as is.
2) Initialize an empty result string and add the first character.
3) Iterate over the string from the second character to the end:
   - Append '*' followed by the current character to the result string.
4) Return the result string.
```

**⚠️ Common Mistakes**

- Not handling empty strings or single-character strings correctly in either approach.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
# Recursive approach (Provided)
def insert_stars_recursive(s):
    if len(s) <= 1:
        return s
    else:
        return s[0] + '*' + insert_stars_recursive(s[1:])

# Iterative approach
def insert_stars_iterative(s):
    if len(s) <= 1:
        return s
    result = s[0]
    for char in s[1:]:
        result += '*' + char
    return result
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with input "hello" to ensure it outputs "h*e*l*l*o".
- Validate the edge case with a single character "h" to check that it returns "h" unchanged.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: Both methods are `O(n)` where `n` is the length of the string, as each character is processed once.
* **Space Complexity**: `O(n)` for the recursive approach due to the recursion stack and `O(n)` for the iterative approach due to the result string size.
