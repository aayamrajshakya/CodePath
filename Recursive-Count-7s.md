*[[Unit 7 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 10 mins
* 🛠️ **Topics**: Recursion, Number Manipulation
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: What should happen if `n` is zero?
  - A: The function should return 0 since there are no occurrences of any digits in 0.

```
HAPPY CASE
Input: 1727647
Output: 2
Explanation: The digit 7 appears twice in the number 1727647.

EDGE CASE
Input: 0
Output: 0
Explanation: The number 0 does not contain any digits of 7.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem falls into a category of counting specific items within a larger structure, utilizing recursion for simplified breakdown:

- Using recursive function calls to peel off digits of the number and count occurrences.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Create a recursive function that checks if the last digit of a number is 7 and then recursively calls itself with the rest of the number.

```markdown
1) Base Case: If `n` is 0, return 0.
2) Recursive Case: Check if the last digit is 7. If it is, add 1 and recurse with `n` divided by 10; otherwise, just recurse with `n` divided by 10.
```

**⚠️ Common Mistakes**

- Forgetting to handle the case where `n` becomes zero, which might lead to incorrect or endless recursion.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def count_sevens(n):
    if n == 0:
        return 0  # Base case: no more digits to check
    elif n % 10 == 7:
        return 1 + count_sevens(n // 10)  # Increment count and recurse on the rest
    else:
        return count_sevens(n // 10)  # Just recurse without incrementing
```
    
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with an input of 1727647 to ensure it correctly counts two occurrences of the digit 7.
- Validate the base case with input 0 to confirm that it returns 0.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(log n)` because the function reduces `n` by a factor of 10 with each recursive call, effectively depending on the number of digits in `n`.
* **Space Complexity**: `O(log n)` due to the recursion stack depth also relating to the number of digits.
