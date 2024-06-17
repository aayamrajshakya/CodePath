*[[Unit 7 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 10 mins
* 🛠️ **Topics**: Recursion, Fibonacci Sequence, Mathematics
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: What should the function return for `n = 0` and `n = 1`?
  - A: According to Fibonacci sequence rules, for `n = 0`, return 0, and for `n = 1`, return 1.

```
HAPPY CASE
Input: 5
Output: 5
Explanation: The 5th Fibonacci number is 5 (sequence: 0, 1, 1, 2, 3, 5).

EDGE CASE
Input: 0
Output: 0
Explanation: The 0th Fibonacci number is defined as 0.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This is a classic recursive problem related to number sequences:

- Utilizing the definition of Fibonacci sequence to create recursive function calls.
- Handling multiple base cases as the sequence has specific values defined for the first two indices.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Develop a recursive function to return the nth Fibonacci number using its mathematical definition.

```markdown
1) Base Case 1: If `n` is 0, return 0.
2) Base Case 2: If `n` is 1, return 1.
3) Recursive Case: Return `fibonacci(n-1) + fibonacci(n-2)`.
```

**⚠️ Common Mistakes**

- Forgetting to implement both base cases, which are crucial for the recursive logic to terminate properly.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def fibonacci(n):
    if n == 0:
        return 0
    elif n == 1:
        return 1
    else:
        return fibonacci(n-1) + fibonacci(n-2)
```
  
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with an input of 5 to ensure it correctly computes the Fibonacci number as 5.
- Validate the base cases with input 0 and 1 to confirm correct returns of 0 and 1, respectively.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(2^n)` due to the exponential number of function calls.
* **Space Complexity**: `O(n)` due to the maximum height of the recursion tree, which equals n.
