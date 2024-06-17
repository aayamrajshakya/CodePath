*[[Unit 7 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 15 mins
* 🛠️ **Topics**: Binary Search, Recursive Algorithms, Arrays
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: What should the function do if the target is not found?
  - A: If the target is not found, the function should return -1 to indicate its absence in the list.

```
HAPPY CASE
Input: nums = [1, 3, 5, 7, 9], target = 5
Output: 2
Explanation: The target value 5 exists in the list at index 2.

EDGE CASE
Input: nums = [1, 3, 5, 7, 9], target = 2
Output: -1
Explanation: The target value 2 does not exist in the list.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem is a classic application of binary search, adapted to a recursive method:

- Understanding the fundamental properties of binary search.
- Implementing it in a recursive fashion, which is a common approach in algorithmic problem-solving.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Develop a recursive binary search function that checks for the presence of a target value within a sorted list.

```markdown
1) Base Case: If the range is exhausted without finding the target, return -1.
2) Calculate the middle index of the current search range.
3) If the middle element is the target, return its index.
4) If the target is less than the middle element, recursively search the left half.
5) If the target is greater than the middle element, recursively search the right half.
```

**⚠️ Common Mistakes**

- Not adjusting the search boundaries correctly, which might skip the target or cause unnecessary recursion.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
"def binary_search(nums, left, right, target):
    if left > right:
        return -1  # Target is not found

    mid = (left + right) // 2
    
    # Found the target, return its index.
    if nums[mid] == target:
        return mid
    
    # Decide to search left or right half.
    if target < nums[mid]:
        return binary_search(nums, left, mid - 1, target)
    else:
        return binary_search(nums, mid + 1, right, target)

def binary_search_recursive(nums, target):
    # Initial call to the external binary search function
    return binary_search(nums, 0, len(nums) - 1, target)"
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with a list [1, 3, 5, 7, 9] and a target of 5 to ensure it correctly identifies index 2.
- Validate with a target not in the list (e.g., 2) to check that it returns -1, correctly handling the edge case.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(log n)` because each recursive call reduces the problem size by half.
* **Space Complexity**: `O(log n)` due to the recursion depth being equal to the logarithm of the list size.
