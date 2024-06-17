*[[Unit 7 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 25 mins
* 🛠️ **Topics**: Divide and Conquer, Recursion, Sorting Algorithms
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: What is the behavior of the merge sort algorithm when dealing with duplicate values?
  - A: Merge sort should handle duplicates without any issues, as it will retain their order relative to each other, ensuring stability.

```
HAPPY CASE
Input: [5,3,8,6,2,7,1,4]
Output: [1,2,3,4,5,6,7,8]
Explanation: The list is sorted in ascending order.

EDGE CASE
Input: [1,1,1,1]
Output: [1,1,1,1]
Explanation: The merge sort should handle arrays of identical elements without changing their order.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem is a classic example of the divide and conquer technique:

- Using recursion to divide the problem into smaller parts, sort each part, and then merge them back together.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Implement the merge sort algorithm, which involves recursively splitting the list into halves until the sublists are trivially sorted (one element), then merge these sorted lists back into a complete sorted list.

```markdown
1) If the list length is 0 or 1, it is already sorted, so return it.
2) Split the list into two halves.
3) Recursively apply merge sort to both halves.
4) Merge the two sorted halves into a single sorted list using the merge function.
5) Return the merged and sorted list.
```

**⚠️ Common Mistakes**

- Not correctly merging the two halves can lead to unsorted segments or missing elements.
- Failing to handle edge cases like empty lists or lists with one element.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def merge_sort(lst):
    if len(lst) <= 1:
        return arr
    
    mid = len(arr) // 2
    left_half = arr[:mid]
    right_half = arr[mid:]
    
    # Recursive calls to merge_sort for sorting the left and right halves
    left_half = merge_sort(left_half)
    right_half = merge_sort(right_half)
    
    return merge(left_half, right_half)
    
def merge(left, right):
    result = [] 
    i = j = 0  
    while i < len(left) and j < len(right):
        if left[i] <= right[j]:
            result.append(left[i])
            i += 1
        else:
            result.append(right[j])
            j += 1
    while i < len(left):
        result.append(left[i])
        i += 1
    while j < len(right):
        result.append(right[j])
        j += 1
    
    return result
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Test with input [5,3,8,6,2,7,1,4] to ensure it sorts correctly to [1,2,3,4,5,6,7,8].
- Check with an array of identical elements [1,1,1,1] to confirm correct handling.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(n log n)` which is typical for merge sort due to the log-linear complexity of dividing and merging.
* **Space Complexity**: `O(n)` due to the space required for storing the temporary subarrays during the merge process.
