*[[Unit 7 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 15 mins
* 🛠️ **Topics**: Recursion, String Validation
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: How should the function handle an empty string?
  - A: An empty string should be considered as correctly nested, so the function should return `True`.

```
HAPPY CASE
Input: "(())"
Output: True
Explanation: The string is a correctly nested pair of parentheses.

EDGE CASE
Input: "(()"
Output: False
Explanation: The string has an unmatched opening parenthesis.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem is a typical string parsing problem that can be elegantly solved with recursion:

- Using recursion to simplify the validation of nested structures.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use a recursive function to validate nested parentheses by checking pairs from the outside inward.

```markdown
1) If the string is empty, return True (base case).
2) If the string starts with '(' and ends with ')', recursively validate the substring between them.
3) Otherwise, return False.
```

**⚠️ Common Mistakes**

- Not considering strings that start or end incorrectly but may still contain correct pairs inside.
- Misidentifying base cases or failing to adequately reduce the problem in each recursive step.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def is_nested_parens(s):
    if s == "":
        return True
    if len(s) >= 2 and s[0] == '(' and s[-1] == ')':
        return is_nested_parens(s[1:-1])
    return False
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Test the function with input "(())" to ensure it returns True.
- Validate with input "(()" and ensure it returns False, correctly handling the edge case.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(n)` because each recursive call processes two fewer characters until the string is empty or invalid.
* **Space Complexity**: `O(n)` due to the recursion stack depth, potentially extending to the length of the string in deeply nested cases.
