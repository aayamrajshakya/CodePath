*[[Unit 10 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 30 mins
* 🛠️ **Topics**: Array, Math
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- What should be returned if `nums` contains only one element?
    - This situation is not possible as the problem guarantees the list contains all numbers from `1` to `n` with one duplicated and one missing.

```
HAPPY CASE
Input: nums = [1, 2, 2, 4]
Output: [2, 3]
Explanation: The number 2 is duplicated and the number 3 is missing.

HAPPY CASE
Input: nums = [1, 1]
Output: [1, 2]
Explanation: The number 1 is duplicated and the number 2 is missing.

EDGE CASE
Input: nums = [2, 2]
Output: [2, 1]
Explanation: The number 2 is duplicated and the number 1 is missing.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

For Array problems, we want to consider the following approaches:

- Using mathematical formulas to find the sum and sum of squares to identify the missing and duplicate numbers.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use the difference between the expected sum and sum of squares of the numbers from `1` to `n` and the actual sum and sum of squares of the given numbers to solve for the missing and duplicate numbers.

```
1) Calculate the expected sum of numbers from `1` to `n` using the formula `n * (n + 1) // 2`.
2) Calculate the expected sum of squares of numbers from `1` to `n` using the formula `n * (n + 1) * (2 * n + 1) // 6`.
3) Calculate the actual sum of the given numbers.
4) Calculate the actual sum of squares of the given numbers.
5) Find the difference between the expected and actual sums (`sum_diff`).
6) Find the difference between the expected and actual sum of squares (`sum_squares_diff`).
7) Use these differences to solve for the missing and duplicate numbers:
    a) `missing_plus_duplicate = sum_squares_diff // sum_diff`
    b) `missing = (sum_diff + missing_plus_duplicate) // 2`
    c) `duplicate = missing_plus_duplicate - missing`
8) Return the duplicate and missing numbers as a list.
```

**⚠️ Common Mistakes**

- Incorrectly calculating the expected sum and sum of squares.
- Not handling large numbers correctly when calculating the differences.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```
def find_error_nums(nums):
    n = len(nums)
    
    # Calculate the expected sum and sum of squares
    expected_sum = n * (n + 1) // 2
    expected_sum_squares = n * (n + 1) * (2 * n + 1) // 6
    
    # Calculate the actual sum and sum of squares
    actual_sum = sum(nums)
    actual_sum_squares = sum(x * x for x in nums)
    
    # Calculate the differences
    sum_diff = expected_sum - actual_sum
    sum_squares_diff = expected_sum_squares - actual_sum_squares
    
    # Solve for the missing and duplicate numbers
    missing_plus_duplicate = sum_squares_diff // sum_diff
    missing = (sum_diff + missing_plus_duplicate) // 2
    duplicate = missing_plus_duplicate - missing
    
    return [duplicate, missing]
```
 
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with an input to check for the expected output.
- Example: Trace with nums = [1, 2, 2, 4]
    - expected_sum = 10, expected_sum_squares = 30
    - actual_sum = 9, actual_sum_squares = 25
    - sum_diff = 1, sum_squares_diff = 5
    - missing_plus_duplicate = 5
    - missing = 3, duplicate = 2
    - Return [2, 3]

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

Assume `N` represents the length of the list `nums`.

* **Time Complexity**: `O(N)` because we need to traverse the list to calculate the sums.
* **Space Complexity**: `O(1)` because we only use a constant amount of extra space.