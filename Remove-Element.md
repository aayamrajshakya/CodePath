*[[Unit 10 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 20 mins
* 🛠️ **Topics**: Array, Two Pointers
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- What should be returned if `nums` is empty?
    - 0, since there are no elements to remove.

```
HAPPY CASE
Input: nums = [3, 2, 2, 3], val = 3
Output: 2
Explanation: After removing 3s, the array becomes [2, 2]. The first 2 elements are [2, 2].

HAPPY CASE
Input: nums = [0,1,2,2,3,0,4,2], val = 2
Output: 5
Explanation: After removing 2s, the array becomes [0,1,3,0,4]. The first 5 elements are [0, 1, 3, 0, 4].

EDGE CASE
Input: nums = [], val = 1
Output: 0
Explanation: The array is empty, so the output is 0.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

For Array problems, we want to consider the following approaches:

- Using two pointers to traverse the array and overwrite the elements to remove occurrences of `val`.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use a pointer `k` to keep track of the position to overwrite elements that are not equal to `val`. Iterate through the array, and when an element is not equal to `val`, overwrite the element at position `k` and increment `k`.

```
1) Initialize a variable `k` to 0 to keep track of the number of elements not equal to `val`.
2) Iterate through each element `i` in the array `nums`:
    a) If `nums[i]` is not equal to `val`:
        i) Overwrite `nums[k]` with `nums[i]`.
        ii) Increment `k`.
3) Return `k`, which represents the number of elements not equal to `val`.
```

**⚠️ Common Mistakes**

- Not correctly handling the case where the array is empty.
- Incorrectly updating the pointers.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```
def remove_element(nums, val):
    k = 0
    for i in range(len(nums)):
        if nums[i] != val:
            nums[k] = nums[i]
            k += 1
    return k
```
 
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with an input to check for the expected output.
- Example: Trace with nums = [3, 2, 2, 3], val = 3
    - k = 0, i = 0
    - nums[0] = 3 (skip)
    - nums[1] = 2, nums[0] = 2, k = 1
    - nums[2] = 2, nums[1] = 2, k = 2
    - nums[3] = 3 (skip)
    - Return k = 2

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

Assume `N` represents the length of the array `nums`.

* **Time Complexity**: `O(N)` because we need to traverse the array once.
* **Space Complexity**: `O(1)` because we only use a constant amount of extra space.