*[[Unit 7 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 15 mins
* 🛠️ **Topics**: Binary Search, Arrays, Iterative Algorithms
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: What should the function return if the array consists entirely of 1's?
  - A: The function should return 0 as there are no 0's in the array.

```
HAPPY CASE
Input: [0, 0, 0, 0, 1, 1, 1]
Output: 4
Explanation: There are four 0's before the first 1 appears.

EDGE CASE
Input: [1, 1, 1, 1, 1]
Output: 0
Explanation: There are no 0's in the array, so the function returns 0.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem is an efficient counting challenge best suited for a binary search technique:

- Using binary search to quickly locate the transition point from 0 to 1, facilitating an immediate count of zeros.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Utilize an iterative binary search to find the index of the first occurrence of 1 in the sorted array.

```markdown
1) Initialize low to 0 and high to the length of the array minus one.
2) While low is less than or equal to high:
   - Calculate the mid index.
   - Check if the mid index is the first occurrence of 1:
     - If nums[mid] is 1 and nums[mid - 1] is 0 (or mid is 0), then count of zeros is mid.
     - If nums[mid] is 0, move the low to mid + 1.
     - Otherwise, move the high to mid - 1.
3) If 1 is never found, return the array length
```

**⚠️ Common Mistakes**

- Failing to correctly identify the first 1 in the presence of multiple 1's and 0's.
- Not handling arrays composed entirely of 0's or 1's.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def count_zeros(nums):
    low, high = 0, len(nums) - 1
    while low <= high:
        mid = (low + high) // 2
        if lst[mid] == 1:
            if mid == 0 or lst[mid - 1] == 0:
                return mid  # Number of 0's is the index of the first '1'
            high = mid - 1
        else:
            low = mid + 1

    return len(nums)  # If no '1' is found, all are zeros
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Test with input [0, 0, 0, 0, 1, 1, 1] to ensure it correctly identifies 4 zeros.
- Validate with an array of all ones [1, 1, 1, 1, 1] to confirm it returns 0.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(log n)` due to the binary search process.
* **Space Complexity**: `O(1)` since no additional space is used beyond variables for the search indices.
