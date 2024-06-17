*[[Unit 7 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 15 mins
* 🛠️ **Topics**: Binary Search, Iterative Algorithms, Arrays
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: What should happen if the target is greater than all elements in the array?
  - A: The function should return the length of the array, indicating that the target should be inserted at the end.

```
HAPPY CASE
Input: nums = [1, 3, 5, 6], target = 5
Output: 2
Explanation: 5 already exists in the array at index 2.

EDGE CASE
Input: nums = [1, 3, 5, 6], target = 7
Output: 4
Explanation: 7 does not exist in the array but would fit at the end, so the index 4 is returned.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem is a fundamental application of binary search:

- Adjusting binary search to not only find elements but also to find where an element should be if it's not present.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use an iterative binary search approach to find either the position of the target or where it would be inserted if not found.

```markdown
1) Initialize `left` to 0 and `right` to the length of the array minus one.
2) While `left` is less than or equal to `right`:
   - Calculate the middle index.
   - If the middle element is the target, return the middle index.
   - If the target is less than the middle element, adjust `right` to `mid - 1`.
   - Otherwise, adjust `left` to `mid + 1`.
3) If the target is not found, `left` will be at the index where the target should be inserted.
```

**⚠️ Common Mistakes**

- Returning the wrong index when the element is not found.
- Overlooking the conditions that adjust the `left` and `right` pointers, leading to incorrect results.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def search_insert(nums, target):
    left, right = 0, len(nums) - 1
    while left <= right:
        mid = (left + right) // 2
        if nums[mid] == target:
            return mid
        elif nums[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    return left
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Test the function with input [1, 3, 5, 6] and target 5 to ensure it finds index 2.
- Validate with target 7 to check that it correctly identifies index 4 as the insertion point.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(log n)` due to the binary search approach.
* **Space Complexity**: `O(1)` as it requires a constant amount of space.
