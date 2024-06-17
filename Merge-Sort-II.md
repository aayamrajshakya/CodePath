*[[Unit 7 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 20 mins
* 🛠️ **Topics**: Divide and Conquer, Recursion, Sorting Algorithms
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: How should `merge()` handle arrays of different lengths?
  - A: `merge()` should be able to merge two sublists of different lengths seamlessly, adding remaining elements from the longer sublist once comparisons are complete.

```
HAPPY CASE
Input: left = [1,3,5], right = [2,4,6]
Output: [1,2,3,4,5,6]
Explanation: The sublists are merged into a single sorted list.

EDGE CASE
Input: left = [1,2,3], right = []
Output: [1,2,3]
Explanation: Since one of the sublists is empty, the merge simply returns the non-empty sublist.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem is a foundational component of the merge sort algorithm:

- Understanding how to merge two sorted lists is essential for implementing the full merge sort algorithm.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Develop a function `merge()` that combines two sorted sublists into one sorted list.

```markdown
1) Initialize an empty list `result`.
2) Use two pointers to track the current index of each sublist (`i` for `left`, `j` for `right`).
3) Compare elements from both sublists and append the smaller one to `result`.
4) If one sublist is exhausted, append the remainder of the other sublist to `result`.
5) Return the `result` list.
```

**⚠️ Common Mistakes**

- Not handling the remaining elements in one of the sublists after the main comparisons are done.
- Failing to maintain the order when merging, leading to an incorrectly sorted result.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def merge(left, right):
    i, j = 0, 0
    result = []
    while i < len(left) and j < len(right):
        if left[i] < right[j]:
            result.append(left[i])
            i += 1
        else:
            result.append(right[j])
            j += 1
    result.extend(left[i:])  # Append remaining elements from left if any
    result.extend(right[j:])  # Append remaining elements from right if any
    return result
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Test the function with inputs [1,3,5] and [2,4,6] to ensure it merges correctly to [1,2,3,4,5,6].
- Check with one empty input [1,2,3] and [] to confirm it returns [1,2,3].

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(n + m)` where `n` and `m` are the lengths of the two sublists, since every element in each list is processed once.
* **Space Complexity**: `O(n + m)` for the space needed to hold the `result` list.
