*[[Unit 7 Session 2]] (Click for link to problem statements)*

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

- Q: What should the function return if the string is empty?
  - A: If the string is empty, the function should return an empty string.

```
HAPPY CASE
Input: s = "banana", char = "a"
Output: "bnn"
Explanation: All instances of 'a' are removed from the string.

EDGE CASE
Input: s = "aaaaa", char = "a"
Output: ""
Explanation: Removing 'a' from a string of only 'a's results in an empty string.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem is a straightforward application of recursive string manipulation:

- Removing characters from a string recursively by breaking down the problem into smaller segments.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use recursion to process each character of the string, removing the specified character and building the result recursively.

```markdown
1) If the string is empty, return an empty string.
2) If the first character of the string is the character to remove, skip it and recursively process the rest of the string.
3) Otherwise, include the first character and recursively process the rest of the string.
4) Combine the results of the recursive calls to build the final string.
```

**⚠️ Common Mistakes**

- Failing to handle the base case where the string is empty, which could result in infinite recursion.
- Incorrectly combining the results, leading to characters not being removed correctly.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def remove_char(s, char):
    if not s:
        return ""
    if s[0] == char:
        return remove_char(s[1:], char)
    else:
        return s[0] + remove_char(s[1:], char)
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Test the function with input ("banana", "a") to ensure it returns "bnn".
- Check the edge case ("aaaaa", "a") to confirm it returns an empty string.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(n)` where `n` is the length of the string since each character is processed once.
* **Space Complexity**: `O(n)` for the recursion stack in the worst case where no characters are removed.
