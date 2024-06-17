*[[Unit 7 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 10 mins
* 🛠️ **Topics**: Binary Search, Iterative Algorithms, Arrays
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: What should be returned if the target is not found in the list?
  - A: The function should return `-1` indicating that the target is not present.

```
HAPPY CASE
Input: lst = [1, 2, 3, 4, 5], target = 3
Output: 2
Explanation: The target value 3 is located at index 2.

EDGE CASE
Input: lst = [1, 2, 3, 4, 5], target = 6
Output: -1
Explanation: The target value 6 is not in the list.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This is a classic binary search problem, requiring an iterative approach to searching in a sorted list:

- Understanding the binary search mechanism.
- Implementing an iterative solution to reduce space complexity.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Implement an iterative binary search that finds the index of a target value within a sorted array.

```markdown
1) Initialize pointers for the left and right bounds of the list.
2) While the left pointer is not greater than the right:
   - Calculate the middle index.
   - If the middle element is the target, return the index.
   - If the target is less than the middle element, adjust the right pointer to narrow the search to the left half.
   - If the target is greater than the middle element, adjust the left pointer to narrow the search to the right half.
3) If the loop exits without finding the target, return -1.
```

**⚠️ Common Mistakes**

- Forgetting to handle the case where the target is not found, which should return `-1`.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def binary_search(lst, target):
    left, right = 0, len(lst) - 1
    
    while left <= right:
        mid = (left + right) // 2
        if lst[mid] == target:
            return mid
        elif lst[mid] > target:
            right = mid - 1
        else:
            left = mid + 1
    
    return -1
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with a list [1, 2, 3, 4, 5] and a target of 3 to ensure it correctly identifies the index 2.
- Validate with a target not in the list (e.g., 6) to check that it returns -1.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(log n)` because each iteration approximately halves the number of elements to be searched.
* **Space Complexity**: `O(1)` because the iterative approach does not use additional space proportional to the input size.
