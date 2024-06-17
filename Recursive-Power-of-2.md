*[[Unit 7 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 15 mins
* 🛠️ **Topics**: Recursion, Mathematics, Powers of Two
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: What should the function return for `n = 0`?
  - A: The function should return `False` since 0 is not a power of two.

```
HAPPY CASE
Input: 8
Output: True
Explanation: (8 = 2^3), hence it is a power of two.

EDGE CASE
Input: 0
Output: False
Explanation: 0 is not a power of any positive integer.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem aligns with a mathematical and recursive decomposition problem, focusing on:

- Understanding properties of powers of two.
- Reducing the problem size by dividing the number recursively.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use a recursive method to determine if a number is a power of two by continuously dividing the number by two.

```markdown
1) Base Case: If `n` is 1, return True because \(2^0 = 1\).
2) If `n` is less than 1 or not divisible by 2, return False.
3) Recursive Case: Recursively call the function with \(n/2\).
```

**⚠️ Common Mistakes**

- Not correctly identifying non-powers of two that are not immediately obvious (e.g., 0 or negative numbers).

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def is_power_of_two(n):
    # Base case: if n is 1, it's a power of 2
    if n == 1:
        return True

    # Base case: if n is less than 1 or not divisible by 2, it's not a power of 2
    elif n < 1 or n % 2 != 0:
        return False

    # Recursive case: recursively check if n divided by 2 is a power of 2
    else:
        return is_power_of_two(n // 2)
        
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with an input of 8 to check for the expected output of True.
- Validate the edge case with input 0 and other non-powers like 3 to ensure the function returns False.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(log n)` because each recursive call reduces the problem size by half.
* **Space Complexity**: `O(log n)` due to the recursion stack depth, also reducing by half each time.
