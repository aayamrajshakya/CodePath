*[[Unit 10 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 20 mins
* 🛠️ **Topics**: Dynamic Programming
* 📺 **Non-TIP101 Version**: [[Climbing Stairs]]
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- How many ways can you climb if `n` is 0?
    - There is 1 way to climb 0 steps (by not climbing at all).

```
HAPPY CASE
Input: n = 2
Output: 2
Explanation: There are two ways to climb to the top: (1 step + 1 step) or (2 steps).

HAPPY CASE
Input: n = 3
Output: 3
Explanation: There are three ways to climb to the top: (1 step + 1 step + 1 step), (1 step + 2 steps), or (2 steps + 1 step).

EDGE CASE
Input: n = 0
Output: 1
Explanation: There is one way to climb 0 steps (by not climbing at all).

EDGE CASE
Input: n = 1
Output: 1
Explanation: There is only one way to climb 1 step (by taking 1 step).
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

For Dynamic Programming problems, we want to consider the following approaches:

- Using a bottom-up approach to store the results of subproblems and build the solution iteratively.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use dynamic programming to store the number of ways to reach each step. The number of ways to reach step `i` is the sum of the ways to reach steps `i-1` and `i-2`.

```
1) If n is 0 or 1, return 1.
2) Initialize two variables, prev2 and prev1, to 1 (ways to reach steps 0 and 1).
3) Iterate from 2 to n:
    a) Calculate the current number of ways as the sum of prev1 and prev2.
    b) Update prev2 to prev1.
    c) Update prev1 to current.
4) Return prev1.
```

**⚠️ Common Mistakes**

- Forgetting to handle the base cases where n is 0 or 1.
- Incorrectly updating the previous steps in the iteration.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```
def climb_stairs(n):
    if n == 0:
        return 1
    elif n == 1:
        return 1
    
    prev2 = 1
    prev1 = 1
    
    for i in range(2, n + 1):
        current = prev1 + prev2
        prev2 = prev1
        prev1 = current
    
    return prev1
```
 
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with an input to check for the expected output.
- Example: Trace with n = 3
    - prev2 = 1, prev1 = 1
    - current = prev1 + prev2 = 2
    - prev2 = 1, prev1 = 2
    - current = prev1 + prev2 = 3
    - prev2 = 2, prev1 = 3
    - Return prev1 = 3

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

Assume `N` represents the number of steps.

* **Time Complexity**: `O(N)` because we need to iterate through the steps.
* **Space Complexity**: `O(1)` because we only use a constant amount of extra space.