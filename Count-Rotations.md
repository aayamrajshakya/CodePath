*[[Unit 7 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 20 mins
* 🛠️ **Topics**: Binary Search, Arrays, Rotations
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: What happens if the array has not been rotated?
  - A: If the array has not been rotated, the function should return 0 as the array's minimum element will be at the first index.

```
HAPPY CASE
Input: [11, 12, 15, 18, 2, 5, 6, 8]
Output: 4
Explanation: The array has been rotated 4 times (the minimum element, 2, is at index 4).

EDGE CASE
Input: [2, 5, 6, 8, 11, 12, 15, 18]
Output: 0
Explanation: The array is not rotated (the minimum element is at index 0).
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem is a variant of binary search, adapted to detect the number of rotations in a circularly sorted array:

- Adapting binary search to find the point of minimum value, which indicates the number of rotations.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use binary search to find the index of the minimum element in the array, which corresponds to the number of rotations.

```markdown
1) Establish pointers for the beginning (`low`) and end (`high`) of the array.
2) If the element at `low` is less than or equal to the element at `high`, the array is not rotated.
3) Use a loop to continue searching as long as `low` is less than `high`:
   - Calculate the middle index (`mid`).
   - Check the relationship between `mid`, `low`, and `high` to determine the unsorted part:
     - If the element at `mid` is greater than the element at `high`, the rotation is in the right half, set `low` to `mid + 1`.
     - Otherwise, set `high` to `mid`.
4) At the end of the loop, `low` will point to the smallest element, which is the number of rotations.
```

**⚠️ Common Mistakes**

- Incorrectly identifying the sorted and unsorted parts of the array, which could lead to missing the minimum element.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def count_rotations(nums):
    low, high = 0, len(nums) - 1
    while low <= high:
        if nums[low] <= nums[high]:  # Array is sorted, no rotation
            return low
        mid = (low + high) // 2
        next_index = (mid + 1) % len(nums)  # circular indexing
        prev_index = (mid - 1 + len(nums)) % len(nums)  # circular indexing
        
        # Check if the mid element is the minimum element
        if nums[mid] <= nums[next_index] and nums[mid] <= nums[prev_index]:
            return mid
        elif nums[mid] > nums[high]:
            low = mid + 1  # Min must be in the right unsorted portion
        else:
            high = mid - 1  # Min must be in the left unsorted portion

    return 0  # This return is technically unreachable due to the logic
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Test the function with input [11, 12, 15, 18, 2, 5, 6, 8] to ensure it returns 4.
- Validate with a non-rotated input [2, 5, 6, 8, 11, 12, 15, 18] to confirm that it correctly identifies 0 rotations.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(log n)` because each iteration of the loop narrows the search range by about half.
* **Space Complexity**: `O(1)` as it uses a constant amount of space.