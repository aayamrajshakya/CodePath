*[[Unit 7 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 20 mins
* 🛠️ **Topics**: Binary Search, Circular Arrays
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: How should the function behave if the target does not exist in the list?
  - A: The function should return -1 if the target is not found.

```
HAPPY CASE
Input: arr = [9, 12, 15, 2, 5, 6, 8], target = 5
Output: 4
Explanation: The target 5 is found at index 4.

EDGE CASE
Input: arr = [9, 12, 15, 2, 5, 6, 8], target = 7
Output: -1
Explanation: The target 7 is not in the list.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem is an extension of the classic binary search applied to a circularly sorted array:

- Understanding how to modify binary search logic to accommodate the rotation in the array.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Implement binary search with additional checks to handle the circular nature of the array.

```markdown
1) Start with pointers at the beginning (`low`) and end (`high`) of the array.
2) While `low` is less than or equal to `high`:
   - Calculate the middle index (`mid`).
   - Check if `mid` is the target. If so, return `mid`.
   - Determine which half of the array is properly sorted:
     - If the left half is sorted (i.e., `arr[low] <= arr[mid]`):
       - If the target lies within this sorted half, adjust `high`.
       - Otherwise, adjust `low`.
     - If the right half is sorted:
       - If the target lies within this sorted half, adjust `low`.
       - Otherwise, adjust `high`.
3) If the loop concludes without finding the target, return -1.
```

**⚠️ Common Mistakes**

- Misidentifying which half of the array is sorted.
- Incorrectly determining if the target is within the sorted half.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def search_in_rotated_array(arr, target):
    low, high = 0, len(arr) - 1
    
    while low <= high:
        mid = (low + high) // 2
        
        if arr[mid] == target:
            return mid
        
        if arr[low] <= arr[mid]:  # Left half is sorted
            if arr[low] <= target < arr[mid]:
                high = mid - 1
            else:
                low = mid + 1
        else:  # Right half is sorted
            if arr[mid] < target <= arr[high]:
                low = mid + 1
            else:
                high = mid - 1
                
    return -1  # Target not found
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Test with input [9, 12, 15, 2, 5, 6, 8] and target 5 to ensure it identifies index 4.
- Validate with target 7 to confirm that it correctly returns -1, correctly handling the edge case.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(log n)` because the algorithm continues to halve the search space despite the array's rotation.
* **Space Complexity**: `O(1)` because it uses a constant amount of space.
