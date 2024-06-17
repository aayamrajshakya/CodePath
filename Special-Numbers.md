*[[Unit 7 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Hard
* ⏰ **Time to complete**: 25 mins
* 🛠️ **Topics**: Binary Search, Arrays, Mathematical Logic
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: What should happen if no such `x` exists?
  - A: If no such `x` exists that fulfills the condition, the function should return -1.

```
HAPPY CASE
Input: nums = [3, 6, 7, 7, 0]
Output: 3
Explanation: There are exactly three numbers that are greater than or equal to 3.

EDGE CASE
Input: nums = [0, 0, 0, 0]
Output: -1
Explanation: There is no number x such that there are x numbers greater than or equal to x.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem involves identifying a special index using an optimized search strategy:

- Using binary search on the number of possible valid counts to efficiently determine if such an \( x \) exists.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use a binary search to find `x` such that there are exactly `x` numbers greater than or equal to `x` by checking possible values for `x`.

```markdown
1) Use binary search on the value range [0, n] where n is the length of the array:
   - For each mid point during the binary search, count how many numbers are greater than or equal to \( mid \).
   - If count equals mid, then mid is the answer.
   - Adjust the binary search bounds based on whether the count is greater or less than \( mid \).
2) Return -1 if no valid x is found.
```

**⚠️ Common Mistakes**

- Not properly handling the relationship between the indices and the elements, especially in arrays with duplicates or all zeros.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def is_special(nums):
    n = len(nums)
    # Traverse from x = 0 to x = len(nums)
    for x in range(n + 1):
        # Find the position in nums where the elements start being >= x
        # Since the list is sorted, we can use the position directly to find how many elements are >= x
        # Binary search can be used here for optimization
        low, high = 0, n
        while low < high:
            mid = (low + high) // 2
            if nums[mid] >= x:
                high = mid
            else:
                low = mid + 1
        # low is now the first index where nums[low] >= x
        # The number of elements >= x is n - low
        if n - low == x:
            return x
    return -1
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Test the function with the input [3, 6, 7, 7, 0] to ensure it returns 3.
- Check the edge case [0, 0, 0, 0] to confirm that it correctly returns -1.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(n log n)` due to the sorting step followed by a binary search operation.
* **Space Complexity**: `O(1)` since the sorting can be in-place and no additional significant space is used.
