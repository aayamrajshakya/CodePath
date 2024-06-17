*[[Unit 7 Session 1]] (Click for link to problem statements)*

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
Input: lst = [1, 3, 5, 7, 9], target = 5
Output: True
Explanation: The target value 5 exists in the list, so the function returns True.

EDGE CASE
Input: lst = [1, 3, 5, 7, 9], target = 2
Output: False
Explanation: The target value 2 does not exist in the list, so the function returns False.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem is a classic application of binary search, using recursion to reduce the search space efficiently:

- Understanding the fundamental properties of binary search.
- Implementing it in a recursive fashion, which is a common approach in algorithmic problem solving.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use binary search to find if the target exists in the list.

```markdown
1) Initialize two pointers, `left` and `right`, at the start and end of the list, respectively.
2) While `left` is less than or equal to `right`:
    a) Compute the middle index `mid`.
    b) If the element at `mid` is the target, return True.
    c) If the target is less than the element at `mid`, adjust `right` to `mid - 1`.
    d) If the target is greater than the element at `mid`, adjust `left` to `mid + 1`.
3) Return False if the target is not found after exhausting the search.
```

**⚠️ Common Mistakes**

- Forgetting to handle the case where the target is not present and should return False.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def binary_search(lst, target):
    # Initialize left and right pointers
    left, right = 0, len(lst) - 1
    
    # Iterate while left pointer is less than or equal to right pointer
    while left <= right:
        # Find the middle index
        mid = (left + right) // 2
        
        # If the middle element is the target, return True
        if lst[mid] == target:
            return True
        # If the target is less than the middle element, search the left half
        elif lst[mid] > target:
            right = mid - 1
        # If the target is greater than the middle element, search the right half
        else:
            left = mid + 1
    
    # If target is not found, return False
    return False
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with an input to check for the expected output
- Catch possible edge cases and off-by-one errors

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

Assume `n` represents the length of the list.

* **Time Complexity**: `O(log n)` because the binary search algorithm halves the search space with each iteration.
* **Space Complexity**: `O(1)` because we only use a few variables for pointer management, without any additional data structures.