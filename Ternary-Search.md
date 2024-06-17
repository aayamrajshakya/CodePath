*[[Unit 7 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 20 mins
* 🛠️ **Topics**: Ternary Search, Arrays, Iterative Algorithms
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: How does the algorithm handle when the target value does not exist in the array?
  - A: The function should return -1 if the target is not found.

```
HAPPY CASE
Input: lst = [1, 2, 5, 8, 12, 15, 18, 22, 27], target = 15
Output: 5
Explanation: The target 15 is located at index 5.

EDGE CASE
Input: lst = [1, 2, 5, 8, 12, 15, 18, 22, 27], target = 20
Output: -1
Explanation: The target value 20 is not in the list.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem is a variation of binary search known as ternary search:

- The array is divided into three parts, and the target is searched in the segment where it may exist based on comparisons.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Implement an iterative ternary search function that divides the search space into three parts instead of two, as in binary search.

```markdown
1) Initialize pointers for the low and high bounds of the array.
2) While the low pointer is less than or equal to the high:
   - Calculate two mid points, mid1 and mid2, that divide the array into three parts.
   - Compare the target with the elements at mid1 and mid2:
     - If the target matches mid1 or mid2, return the index.
     - Adjust pointers based on whether the target is less than mid1, between mid1 and mid2, or greater than mid2.
3) If the loop exits without finding the target, return -1.
```

**⚠️ Common Mistakes**

- Incorrectly calculating mid1 and mid2 such that they do not properly divide the array into three parts.
- Not handling the comparisons correctly which could skip over the target.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def ternary_search(lst, target):
    low, high = 0, len(lst) - 1
    
    while low <= high:
        # Divide the range into three parts
        mid1 = low + (high - low) // 3
        mid2 = high - (high - low) // 3
        
        # Check if the target is found at any mid
        if lst[mid1] == target:
            return mid1  # Target found at mid1
        if lst[mid2] == target:
            return mid2  # Target found at mid2
        
        # Narrow down the search range based on the comparison
        if target < lst[mid1]:
            high = mid1 - 1  # Target in the first third
        elif target > lst[mid2]:
            low = mid2 + 1  # Target in the third third
        else:
            low = mid1 + 1  # Target in the middle third
            high = mid2 - 1
    
    return -1  # Target not found
```
  
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with a list [1, 2, 5, 8, 12, 15, 18, 22, 27] and a target of 15 to ensure it identifies the correct index.
- Validate with a target not in the list (e.g., 20) to check that it returns -1.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(log_3 n)` (base 3), because it divides the search space into thirds each time.
* **Space Complexity**:  `O(1)`, because the solution only uses a few variables to store the indices and comparison results, regardless of the size of the input array.
