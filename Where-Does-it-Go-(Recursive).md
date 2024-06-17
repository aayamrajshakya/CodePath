*[[Unit 7 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 20 mins
* 🛠️ **Topics**: Binary Search, Recursion, Arrays
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: What should happen if all elements in the array are greater than the target?
  - A: The function should return 0, indicating that the target should be inserted at the beginning of the array.

```
HAPPY CASE
Input: nums = [1, 3, 5, 6], target = 5
Output: 2
Explanation: 5 is found at index 2.

EDGE CASE
Input: nums = [1, 3, 5, 6], target = 2
Output: 1
Explanation: 2 is not in the array but would fit at index 1.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem is a classic application of binary search:

- Modifying binary search to not only find an element but also to determine the correct insertion point for an element not found.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use recursive binary search to find the target or determine the appropriate insertion index if the target is not found.

```markdown
1) If the current search bounds are invalid (left > right), return the current left index as the insertion point.
2) Calculate the middle index.
3) If the middle element is the target, return the middle index.
4) If the target is less than the middle element, recursively search the left half.
5) Otherwise, recursively search the right half.
```

**⚠️ Common Mistakes**

- Incorrectly calculating the insertion index when the element is not found.
- Returning the wrong index if the array boundaries are exceeded.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def search_insert_recursive(nums, target):
    # Helper function defined below
    return binary_search(nums, 0, len(nums) - 1, target)

def binary_search(nums, left, right, target):
    if left > right:
        # If we exit the loop without finding the target,
        # 'left' will be at the correct insertion position.
        return left

    mid = (left + right) // 2

    # Found the target, return its index.
    if nums[mid] == target:
        return mid
    
    # Recurse into the appropriate half of the array.
    if target < nums[mid]:
        return binary_search(nums, left, mid - 1, target)
    else:
        return binary_search(nums, mid + 1, right, target)
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Test with input ([1, 3, 5, 6], 5) to ensure it finds index 2.
- Validate with input ([1, 3, 5, 6], 2) to check that it correctly identifies index 1 as the insertion point.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(log n)` due to the binary search mechanism.
* **Space Complexity**: `O(log n)` for the recursion stack, which can grow with the depth of the search.
