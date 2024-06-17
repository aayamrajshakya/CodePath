*[[Unit 7 Session 2]] (Click for link to problem statements)*

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

- Q: What happens if there are no 1's in the array?
  - A: The function should return 0, indicating that there are no 1's.

```
HAPPY CASE
Input: [0, 0, 0, 1, 1, 1, 1]
Output: 4
Explanation: There are four 1's in the array.

EDGE CASE
Input: [0, 0, 0, 0, 0]
Output: 0
Explanation: There are no 1's in the array.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This is an application of binary search to efficiently locate the first occurrence of 1 in a sorted array of 0's and 1's:

- Utilizing binary search to minimize the number of elements inspected, which is particularly useful when dealing with large datasets.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Employ binary search to find the first index where 1 appears and then calculate the count of 1's based on its position.

```markdown
1) If the last element of the array is 0, return 0.
2) Use binary search to find the first occurrence of 1.
3) If 1 is found, subtract its index from the length of the array to get the count of 1's.
4) If no 1 is found during the search, return 0.
```

**⚠️ Common Mistakes**

- Not correctly handling arrays that contain only 0's or only 1's.
- Incorrectly implementing binary search that may skip over the transition from 0 to 1.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def count_ones(lst):
    low, high = 0, len(lst) - 1
    while low <= high:
        mid = (low + high) // 2
        if lst[mid] == 0:
            low = mid + 1
        else:
            high = mid - 1
    
    # Check if low is within the array bounds and points to a 1
    if low < len(lst) and lst[low] == 1:
        return len(lst) - low
    return 0
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Test the function with inputs like [0, 0, 0, 1, 1, 1, 1] to ensure it returns 4.
- Check with an input of [0, 0, 0, 0, 0] to confirm that it correctly identifies the absence of 1's.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(log n)` due to the binary search approach.
* **Space Complexity**: `O(1)` as it requires constant space regardless of the input size.
