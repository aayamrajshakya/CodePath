*[[Unit 7 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 10 mins
* 🛠️ **Topics**: Recursion, Mathematical Problems, Factorials
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: How should the function handle negative inputs?
  - A: The factorial function is traditionally defined for non-negative integers, so a negative input could either not be allowed or handled separately.

```
HAPPY CASE
Input: 5
Output: 120
Explanation: The factorial of 5 is 5 * 4 * 3 * 2 * 1 = 120.

EDGE CASE
Input: 0
Output: 1
Explanation: The factorial of 0 is defined as 1.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

For factorial computation problems, we can use:

- Direct recursive function calls implementing the mathematical definition of factorial.
- Consideration of special cases like the factorial of 0.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use recursion to compute the factorial based on its definition.

```markdown
1) Base Case: If `n` is 0, return 1 (since 0! = 1).
2) Recursive Case: Return `n * factorial(n - 1)`.
```

**⚠️ Common Mistakes**

- Forgetting the base case for 0 which might result in an incorrect or infinite recursion.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def factorial(n):
    if n == 0:
        return 1
    return n * factorial(n-1)
```
    
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with an input of 5 to ensure each recursive call is calculated correctly and aggregates to 120.
- Validate the base case with input 0, which should return 1 directly.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(n)` because we make `n` recursive calls.
* **Space Complexity**: `O(n)` because each recursive call adds a layer to the call stack, using more memory.
