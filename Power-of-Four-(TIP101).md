*[[Unit 10 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 15 mins
* 🛠️ **Topics**: Math, Loop
* 📺 **Non-TIP101 Version**: [[Power of Four]]
* 🗒️ **Similar Question**: [[Recursive Power of 4]] *(Unit 7 Session 1)*

## 1: U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- What should be returned if `n` is less than or equal to zero?
    - Return `False`, since a power of four must be a positive integer.

```
HAPPY CASE
Input: n = 16
Output: True
Explanation: 16 is 4^2.

HAPPY CASE
Input: n = 5
Output: False
Explanation: 5 is not a power of four.

EDGE CASE
Input: n = 1
Output: True
Explanation: 1 is 4^0.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

For problems involving powers, we want to consider the following approaches:

- Using loops to divide the number by 4 repeatedly and check if it reduces to 1.
- Using bit manipulation to check if the number is a power of four.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Continuously divide the number by 4 and check if it eventually reduces to 1.

```
1) If n is less than or equal to 0, return False.
2) While n is divisible by 4, divide n by 4.
3) If n is equal to 1 after the loop, return True.
4) Otherwise, return False.
```

**⚠️ Common Mistakes**

- Not correctly handling the case where n is less than or equal to zero.
- Incorrectly updating the value of n in the loop.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```
def is_power_of_four(n):
    if n <= 0:
        return False
    while n % 4 == 0:
        n //= 4
    return n == 1
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with an input to check for the expected output.
- Example: Trace with n = 16
    - n = 16, n % 4 == 0, n //= 4 -> n = 4
    - n = 4, n % 4 == 0, n //= 4 -> n = 1
    - n = 1, return True

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

Assume `N` represents the value of the integer.

* **Time Complexity**: `O(log N)` because we repeatedly divide the number by 4.
* **Space Complexity**: `O(1)` because we only use a constant amount of extra space.