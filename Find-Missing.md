*[[Unit 7 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 15 mins
* 🛠️ **Topics**: Binary Search, Arrays
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: What happens if there are no missing numbers?
  - A: If no numbers are missing, the missing number would logically be \( n \), since the numbers are from 0 to \( n-1 \).

```
HAPPY CASE
Input: nums = [0, 1, 3, 4, 5]
Output: 2
Explanation: The number 2 is missing in the sequence.

EDGE CASE
Input: nums = [0, 1, 2, 3, 4]
Output: 5
Explanation: Since no numbers are missing from 0 to 4, the missing number is 5.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem is a variant of the classic binary search:

- Adapting binary search to detect an inconsistency in an otherwise complete series of sequential numbers.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use binary search to efficiently find the missing number in a series that is nearly complete.

```markdown
1) Establish binary search bounds with `left` at 0 and `right` at the last index of the array.
2) While `left` is less than `right`:
   - Compute the middle index.
   - If the element at the middle index matches the index, adjust `left` to `mid + 1`.
   - Otherwise, adjust `right` to `mid`.
3) The missing number will be at the position indicated by `left` after the loop completes.
```

**⚠️ Common Mistakes**

- Not considering the possibility that the missing number could be at the very end of the sequence (i.e., \( n \)).

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def find_missing(nums):
    left, right = 0, len(nums)
    while left < right:
        mid = (left + right) // 2
        if nums[mid] > mid:
            right = mid
        else:
            left = mid + 1

    return left
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Test with input [0, 1, 3, 4, 5] to confirm it finds the missing number 2.
- Check with input [0, 1, 2, 3, 4] to ensure it returns 5, demonstrating that it correctly identifies the next logical missing number.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(log n)` because each iteration of the loop narrows the search space by half.
* **Space Complexity**: `O(1)` as the space used does not scale with the size of the input.
