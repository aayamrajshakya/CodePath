*[[Unit 7 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 20 mins
* 🛠️ **Topics**: Divide and Conquer, Recursion, Majority Element Problem
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: What happens if no single element appears more than ⌊n/2⌋ times?
  - A: By problem constraints, it’s given that a majority element always exists in the array, so there’s always an answer.

```
HAPPY CASE
Input: [3, 2, 3]
Output: 3
Explanation: 3 appears more than ⌊3/2⌋ = 1 times.

EDGE CASE
Input: [2, 2, 1, 1, 1, 2, 2]
Output: 2
Explanation: 2 appears more than ⌊7/2⌋ = 3 times.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem is a classic case for the divide and conquer approach:

- Splitting the array and finding the majority element in each half recursively.
- Combining results from two halves to determine the overall majority element.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Recursively divide the array into halves, find the majority element in each half, and then determine the majority for the entire segment by counting.

```markdown
1) Divide the array into two halves, breaking the problem into smaller sub-problems.
2) Recursively find the majority element in each half.
3) Once you have potential majority elements 
  - Use a helper function to count the occurrences of these two candidates in the original segment.
4) Determine which candidate is the true majority by comparing their counts.
  - Return the candidate that has the higher count
```

**⚠️ Common Mistakes**

- Failing to handle cases where two halves have different majority elements.
- Incorrectly counting occurrences in the combined step.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def count_frequency(nums, num, start, end):
    """ Counts how many times 'num' appears in 'nums' between 'start' and 'end' inclusive. """
    count = 0
    for i in range(start, end + 1):
        if nums[i] == num:
            count += 1
    return count

def find_majority(nums, left, right):
    """ Recursively finds the majority element in nums between left and right indices. """
    # Base case: single element, the majority element is trivially the element itself
    if left == right:
        return nums[left]

    # Recursively find the majority element in the left and right halves
    mid = (left + right) // 2
    left_majority = find_majority(nums, left, mid)
    right_majority = find_majority(nums, mid + 1, right)

    # If the two halves agree on the majority, return it
    if left_majority == right_majority:
        return left_majority

    # Count each majority candidate in the entire current range
    left_count = count_frequency(nums, left_majority, left, right)
    right_count = count_frequency(nums, right_majority, left, right)

    # Return the element with the higher count
    if left_count > right_count:
        return left_majority
    else:
        return right_majority

def majority_element(nums):
    """ Uses divide and conquer to find the majority element in nums. """
    return find_majority(nums, 0, len(nums) - 1)
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Test the function with inputs [3, 2, 3] to ensure it correctly identifies 3 as the majority.
- Check with input [2, 2, 1, 1, 1, 2, 2] to confirm that it correctly identifies 2 as the majority.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(n log n)` due to the recursive division of the array and the counting process within each divided segment.
* **Space Complexity**: `O(log n)` due to the recursion stack space required for the divide and conquer process.
