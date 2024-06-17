*[[Unit 7 Session 1]] (Click for link to problem statements)*

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

- Q: What should the function do if the target appears multiple times in the list?
  - A: The function should return the index of the last occurrence of the target.

```
HAPPY CASE
Input: lst = [1, 2, 3, 3, 3, 4, 5], target = 3
Output: 4
Explanation: The last occurrence of the target 3 is at index 4.

EDGE CASE
Input: lst = [1, 2, 3, 4, 5], target = 6
Output: -1
Explanation: The target value 6 is not in the list.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem is a variation of the binary search algorithm, requiring:

- Modifying the classic binary search to continue searching even after finding the target to ensure it is the last occurrence.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Adapt the binary search to locate the last occurrence of a target value within a sorted array.

```markdown
1) Initialize pointers for the left and right bounds of the list.
2) Initialize a variable `last_occurrence` to store the index of the last found target.
3) While the left pointer is not greater than the right:
   - Calculate the middle index.
   - If the middle element is the target, update `last_occurrence` and move the left pointer to continue searching on the right for possible later occurrences.
   - If the target is less than the middle element, adjust the right pointer to narrow the search to the left half.
   - If the target is greater than the middle element, adjust the left pointer to narrow the search to the right half.
4) Return `last_occurrence` if found; otherwise, return -1.
```

**⚠️ Common Mistakes**

- Stopping the search upon finding the first instance of the target without ensuring it is the last occurrence.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def find_last(lst, target):
    left, right = 0, len(lst) - 1
    last_occurrence = -1
    
    while left <= right:
        mid = (left + right) // 2
        
        if lst[mid] == target:
            last_occurrence = mid
            left = mid + 1  # Continue searching in the right half
        elif lst[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    
    return last_occurrence
```
  
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with a list [1, 2, 3, 3, 3, 4, 5] and a target of 3 to ensure it correctly identifies the last occurrence at index 4.
- Validate with a target not in the list (e.g., 6) to check that it returns -1.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(log n)` because the approach still fundamentally relies on binary search, halving the search space with each iteration.
* **Space Complexity**: `O(1)` because it uses a few variables for pointers and does not require additional space based on input size.
