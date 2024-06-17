*[[Unit 7 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 10 mins
* 🛠️ **Topics**: Recursion, Mathematical Logic, Powers
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: What should be the function's behavior for `n = 0` or negative values?
  - A: For `n = 0`, return `True` (since \(1 = 4^0\)), and for negative values, return `False` as they cannot be powers of a positive number.

```
HAPPY CASE
Input: 16
Output: True
Explanation: 16 is a power of four (\(16 = 4^2\)).

EDGE CASE
Input: 0
Output: True
Explanation: 0 can be considered as \(4^0 = 1\) (not zero, correct to \(1 = 4^0\)).
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This is a straightforward recursive problem where the strategy is:

- Using mathematical properties to determine if a number is a power of another.
- Utilizing recursive calls to continuously divide the number by four until a base case is reached.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Implement a recursive function that checks if a number can be divided by four without leaving a remainder until it is reduced to 1.

```markdown
1) Base Case 1: If `n` is 1, return True (since \(1 = 4^0\)).
2) Base Case 2: If `n` is less than 1 or if `n` modulo 4 is not zero, return False.
3) Recursive Case: Return a recursive call with `n` divided by 4.
```

**⚠️ Common Mistakes**

- Incorrectly handling `n = 0` and negative numbers.
- Stopping the recursion without checking all conditions.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def is_power_of_four(n):
    if n == 1:
        return True
    if n < 1 or n % 4 != 0:
        return False
    return is_power_of_four(n // 4)
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Test the function with inputs like 16 to verify that it returns True.
- Ensure that inputs like 0 and negative numbers return False, matching the corrected understanding and typical mathematical definition.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(log n)` in base 4, since we reduce `n` by a factor of 4 with each recursive call.
* **Space Complexity**: `O(log n)` in base 4, due to the recursion stack size being proportional to how many times `n` can be divided by 4.
