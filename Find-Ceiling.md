*[[Unit 7 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 15 mins
* 🛠️ **Topics**: Binary Search, Arrays, Ceiling Calculation
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: What should the function return if all elements in the array are greater than x?
  - A: The function should return -1 as there would be no ceiling within the array.

```
HAPPY CASE
Input: lst = [1, 2, 8, 10, 12, 19], x = 5
Output: 8
Explanation: The smallest element greater than or equal to 5 is 8.

EDGE CASE
Input: lst = [1, 2, 3, 4, 5], x = 6
Output: -1
Explanation: All elements are less than 6, so no ceiling exists.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem is a typical application of the binary search technique in a non-standard context:

- Adapting binary search to find the smallest element greater than or equal to a given number in a sorted list.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use a modified binary search to find the ceiling of x in a sorted array.

```markdown
1) Initialize pointers for the low and high bounds of the array.
2) Maintain a variable to store the potential ceiling value.
3) While the low pointer is less than or equal to the high:
   - Calculate the middle index.
   - If the middle element is less than x, shift the low pointer to mid + 1.
   - Else, update the ceiling to the middle element and shift the high pointer to mid - 1.
4) Return the stored ceiling value if found, otherwise return -1 if the loop concludes without finding a suitable ceiling.
```

**⚠️ Common Mistakes**

- Failing to update the ceiling value correctly during the search.
- Not returning -1 when no valid ceiling is found.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def find_ceiling(lst, x):
    low, high = 0, len(lst) - 1
    result = -1  # Default result if no ceiling is found
    
    while low <= high:
        mid = (low + high) // 2
        if lst[mid] < x:
            low = mid + 1  # Search right if the mid value is less than x
        else:
            result = mid  # Update result to current mid (potential ceiling)
            high = mid - 1  # Continue to search left to find a smaller ceiling
    
    return result
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with a list [1, 2, 8, 10, 12, 19] and x = 5 to ensure it identifies 8 as the ceiling.
- Validate with x = 6 in a list [1, 2, 3, 4, 5] to check that it returns -1, correctly handling the edge case.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(log n)` because the algorithm still utilizes a binary search approach, which divides the search space in half each iteration.
* **Space Complexity**: `O(1)` as the solution does not require extra space beyond a few counter variables.
