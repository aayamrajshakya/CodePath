*[[Unit 7 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 25 mins
* 🛠️ **Topics**: Sorting Algorithms, Divide and Conquer, Recursion
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: How should the function handle an array of a single element?
  - A: The function should return the array as-is since a single-element array is already sorted.

```
HAPPY CASE
Input: [4, 1, 5, 2, 6, 3, 7]
Output: [1, 2, 3, 4, 5, 6, 7]
Explanation: The array is sorted in ascending order.

EDGE CASE
Input: [1]
Output: [1]
Explanation: A single-element array is returned unchanged as it is already sorted.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem is a classic example of the divide and conquer approach:

- Splitting the array recursively into smaller parts, sorting those parts, and then merging them back together in sorted order.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Implement the merge sort algorithm, which involves recursively splitting the list into halves until the sublists contain a single element, then merge these sorted lists back into a complete sorted list.

```markdown
1) If the length of the list is 0 or 1, return the list as it is already sorted.
2) Divide the list into two halves.
3) Recursively apply merge sort to both halves.
4) Merge the two sorted halves.
5) Return the merged and sorted list.
```

**⚠️ Common Mistakes**

- Not handling the recursive base case correctly could lead to infinite recursion.
- Mismanaging the merging process can result in an unsorted final list.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def merge_sort(arr):
    if len(arr) <= 1:
        return arr

    mid = len(arr) // 2
    left_half = merge_sort(arr[:mid])
    right_half = merge_sort(arr[mid:])

    return merge(left_half, right_half)

def merge(left, right):
    sorted_list = []
    i = j = 0
    while i < len(left) and j < len(right):
        if left[i] < right[j]:
            sorted_list.append(left[i])
            i += 1
        else:
            sorted_list.append(right[j])
            j += 1
    sorted_list.extend(left[i:])
    sorted_list.extend(right[j:])
    return sorted_list
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Test the function with input [4, 1, 5, 2, 6, 3, 7] to ensure it sorts correctly to [1, 2, 3, 4, 5, 6, 7].
- Check with a single-element array [1] to confirm it returns [1] without change.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(n log n)` due to the divide and conquer approach, where the division of the array and the merging process each take logarithmic steps multiplied by linear work for merging.
* **Space Complexity**: `O(n)` due to the additional space required for the temporary arrays used in the merge step.
