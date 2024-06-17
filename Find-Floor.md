*[[Unit 7 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 15 mins
* 🛠️ **Topics**: Binary Search, Mathematics, Arrays
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: What should be returned if there is no floor value for x in the array?
  - A: The function should return `None` if no element is smaller than or equal to x.

```
HAPPY CASE
Input: arr = [1, 2, 8, 10, 10, 12, 19], x = 5
Output: 2
Explanation: The largest element smaller than or equal to 5 is 2.

EDGE CASE
Input: arr = [1, 2, 8, 10, 10, 12, 19], x = 0
Output: None
Explanation: There is no element in the array smaller than or equal to 0.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem is an application of the binary search technique in a slightly different context:

- Adapting binary search to find the "floor" value of a given number in a sorted list.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use a modified binary search to identify the largest number in a sorted array that is less than or equal to a given number x.

```markdown
1) Initialize pointers for the low and high bounds of the array.
2) Initialize a variable `floor_value` to None to track the highest value encountered that is <= x.
3) While the low pointer is not greater than the high:
   - Calculate the middle index.
   - If the middle element is less than or equal to x, update `floor_value` and shift the low pointer to the right to look for a possibly higher floor value.
   - If the middle element is greater than x, shift the high pointer to the left.
4) Return `floor_value`.
```

**⚠️ Common Mistakes**

- Not updating the `floor_value` correctly or failing to continue the search for a higher floor value after finding an initial candidate.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def find_floor(arr, x):
    low, high = 0, len(arr) - 1
    floor_value = None  # Initialize to None to handle the case where all elements are greater than x

    while low <= high:
        mid = (low + high) // 2
        
        if arr[mid] <= x:
            floor_value = arr[mid]  # arr[mid] could be a potential floor
            low = mid + 1  # Look for a larger element that might also be a floor
        else:
            high = mid - 1  # Search in the left half
    
    return floor_value
```
    
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with an array [1, 2, 8, 10, 10, 12, 19] and x = 5 to ensure it identifies 2 as the floor value.
- Validate with x = 0 to check that it returns None, correctly handling the edge case.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(log n)` because the algorithm still utilizes a binary search approach, which divides the search space in half each iteration.
* **Space Complexity**: `O(1)` as the solution does not require extra space proportional to the input size.
