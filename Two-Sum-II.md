*[[Unit 10 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 20 mins
* 🛠️ **Topics**: Two Pointers, Array
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- How should the solution handle duplicates in the array?
    - Duplicates are allowed as long as `index1` and `index2` are not the same and the sum equals the target.

```
HAPPY CASE
Input: numbers = [2, 7, 11, 15], target = 9
Output: [0, 1]
Explanation: The numbers at indices 0 and 1 sum up to 9.

HAPPY CASE
Input: numbers = [1, 2, 3, 4, 4, 9], target = 8
Output: [3, 4]
Explanation: The numbers at indices 3 and 4 sum up to 8.

EDGE CASE
Input: numbers = [-1, 0], target = -1
Output: [0, 1]
Explanation: The numbers at indices 0 and 1 sum up to -1.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

For Array problems, we want to consider the following approaches:

- Using two pointers to traverse the array from both ends towards the center, checking sums.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use two pointers, one starting at the beginning and one at the end of the array. Calculate the sum of the values at the two pointers. If the sum equals the target, return the indices. If the sum is less than the target, move the left pointer to the right. If the sum is greater than the target, move the right pointer to the left.

```
1) Initialize two pointers, left to 0 and right to the length of the array minus 1.
2) While left is less than right:
    a) Calculate the sum of the values at the left and right pointers.
    b) If the sum equals the target, return the indices [left, right].
    c) If the sum is less than the target, increment the left pointer.
    d) If the sum is greater than the target, decrement the right pointer.
3) If no solution is found, return an empty list (though the problem guarantees one valid solution).
```

**⚠️ Common Mistakes**

- Not correctly updating the pointers.
- Assuming there could be more than one solution.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```
def two_sum(numbers, target):
    left, right = 0, len(numbers) - 1
    
    while left < right:
        current_sum = numbers[left] + numbers[right]
        if current_sum == target:
            return [left, right]
        elif current_sum < target:
            left += 1
        else:
            right -= 1
```
 
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with an input to check for the expected output.
- Example: Trace with numbers = [2, 7, 11, 15], target = 9
    - left = 0, right = 3
    - current_sum = 2 + 15 = 17, right -= 1
    - current_sum = 2 + 11 = 13, right -= 1
    - current_sum = 2 + 7 = 9, return [0, 1]

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

Assume `N` represents the length of the array `numbers`.

* **Time Complexity**: `O(N)` because we need to traverse the array with two pointers.
* **Space Complexity**: `O(1)` because we only use a constant amount of extra space.