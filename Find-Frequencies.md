*[[Unit 7 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 20 mins
* 🛠️ **Topics**: Binary Search, Arrays, Optimization
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: What should the function return if the array is empty?
  - A: The function should return an empty dictionary as there are no elements to count.

```
HAPPY CASE
Input: [1, 2, 2, 3, 3, 3, 4]
Output: {1: 1, 2: 2, 3: 3, 4: 1}
Explanation: The frequencies of each element are returned.

EDGE CASE
Input: []
Output: {}
Explanation: An empty array results in an empty frequency dictionary.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem requires an efficient way to count the occurrences of each element in a sorted list:

- Leveraging binary search to quickly locate the first and last occurrence of each element for counting.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use a modified binary search to find the first and last index of each unique element and then calculate the difference to get the count.

```markdown
1) Use a helper function to perform binary search to find the first occurrence of each element.
2) Use another helper function to find the last occurrence.
3) The difference between the last and first index, plus one, gives the count of the element.
4) Iterate over the array and apply the above steps to each unique element.
```

**⚠️ Common Mistakes**

- Not handling cases where an element appears only once.
- Overlapping or redoing searches for the same element leading to inefficiency.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def find_first(nums, target):
    lo, hi = 0, len(nums) - 1
    while lo <= hi:
        mid = (lo + hi) // 2
        if nums[mid] < target:
            lo = mid + 1
        elif nums[mid] > target or (mid > 0 and nums[mid-1] == target):
            hi = mid - 1
        else:
            return mid
    return -1

def find_last(nums, target):
    lo, hi = 0, len(nums) - 1
    while lo <= hi:
        mid = (lo + hi) // 2
        if nums[mid] > target:
            hi = mid - 1
        elif nums[mid] < target or (mid < len(nums) - 1 and nums[mid+1] == target):
            lo = mid + 1
        else:
            return mid
    return -1

def find_frequencies(nums):
    frequencies = {}
    i = 0
    while i < len(nums):
        if nums[i] in frequencies:
            i += 1
            continue
        first = find_first(nums, nums[i])
        last = find_last(nums, nums[i])
        frequencies[nums[i]] = last - first + 1
        i = last + 1
    return frequencies
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Test with input [1, 2, 2, 3, 3, 3, 4] to ensure it returns correct frequencies.
- Validate with an empty list to confirm it returns an empty dictionary.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(n log n)` in the worst case when each element is found using binary search.
* **Space Complexity**: `O(1)` for space, not considering the output dictionary.
