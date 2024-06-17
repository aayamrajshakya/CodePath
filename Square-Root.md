*[[Unit 7 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 15 mins
* 🛠️ **Topics**: Binary Search, Mathematics
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: How should the function handle very small values, like 0 or 1?
  - A: The function should return the input itself for 0 and 1, as the square root of 0 is 0 and of 1 is 1.

```
HAPPY CASE
Input: 16
Output: 4
Explanation: The square root of 16 is 4, which is a perfect square.

EDGE CASE
Input: 27
Output: 5
Explanation: The square root of 27 is approximately 5.196, so the floor value is 5.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This is a number computation problem that can effectively be solved using binary search to find the floor of the square root:

- Utilizing binary search to narrow down the possible values for the square root.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Implement a binary search to find the largest integer whose square is less than or equal to the given number.

```markdown
1) If `x` is 0 or 1, return `x` as the square root is the number itself.
2) Initialize the search range with `left` = 1 and `right` = x / 2.
3) While `left` is less than or equal to `right`:
   - Calculate the middle value (`mid`).
   - Compute the square of `mid`.
   - If the square is exactly `x`, return `mid`.
   - If the square is less than `x`, adjust `left` to `mid + 1`.
   - If the square is more than `x`, adjust `right` to `mid - 1`.
4) Return `right` as the largest integer whose square is less than `x`.
```

**⚠️ Common Mistakes**

- Not adjusting the binary search bounds correctly could lead to infinite loops or incorrect results.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def sqrt(x):
    if x < 2:
        return x
    left, right = 1, x // 2
    while left <= right:
        mid = (left + right) // 2
        mid_squared = mid * mid
        if mid_squared == x:
            return mid
        elif mid_squared < x:
            left = mid + 1
        else:
            right = mid - 1
    return right
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Test the function with input 16 to ensure it returns 4.
- Validate the function with input 27 to check that it returns 5 as the floor of the square root.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(log n)` due to the binary search process, which halves the search range with each iteration.
* **Space Complexity**: `O(1)` as it only uses a few variables for computation.
