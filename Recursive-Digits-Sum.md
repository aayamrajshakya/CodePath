*[[Unit 7 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 10 mins
* 🛠️ **Topics**: Recursion, Arithmetic Operations
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: What should the function return for `n = 0`?
  - A: The function should return 0, as the sum of the digits of 0 is 0.

```
HAPPY CASE
Input: 12345
Output: 15
Explanation: The sum of the digits 1 + 2 + 3 + 4 + 5 = 15.

EDGE CASE
Input: 0
Output: 0
Explanation: The sum of the digits in 0 is 0.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem is an example of recursive decomposition used to solve a numerical breakdown problem:

- Recursively stripping the last digit and summing it to a running total.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Develop a recursive function that sums the digits of a given number by repeatedly dividing the number by 10 and adding the remainder.

```markdown
1) Base Case: If `n` is 0, return 0.
2) Recursive Case: Return the last digit (n % 10) plus a recursive call on the rest of the number (n // 10).
```

**⚠️ Common Mistakes**

- Forgetting the base case, which might lead to incorrect recursion termination.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def sum_of_digits(n):
    if n == 0:
        return 0
    else:
        return (n % 10) + sum_of_digits(n // 10)
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with an input of 12345 to ensure it correctly calculates the sum as 15.
- Validate the base case with input 0 to confirm that it returns 0.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(log n)` since the number of recursive calls depends on the number of digits in `n`.
* **Space Complexity**: `O(log n)` due to the recursion stack depth, which also correlates with the number of digits.
