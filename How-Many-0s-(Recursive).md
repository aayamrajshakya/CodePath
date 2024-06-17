*[[Unit 7 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 20 mins
* 🛠️ **Topics**: Binary Search, Recursion, Arrays
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: How should the function behave if the entire array contains only 1s?
  - A: The function should return 0 since there are no 0s present.

```
HAPPY CASE
Input: [0, 0, 0, 0, 1, 1, 1]
Output: 4
Explanation: There are four 0's before the first 1 appears.

EDGE CASE
Input: [1, 1, 1, 1, 1]
Output: 0
Explanation: No zeros are present in the array.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem leverages binary search within a recursive strategy:

- Adapting binary search to identify the transition from 0 to 1, which allows efficient counting of zeros.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Utilize a recursive binary search method to locate the first occurrence of 1 and then compute the number of 0s based on its position.

```markdown
1) Establish a recursive function to perform binary search and find the first 1's index.
2) Base Case: If the search space is exhausted, handle cases based on the position and the element found.
3) Recursive Steps:
   - Calculate the mid-point.
   - If mid-point is 1 and it's the first element or the previous is 0, return its index.
   - Adjust the search range based on whether the mid-point element is 0 or 1.
4) Use the index returned to calculate the number of 0s.
```

**⚠️ Common Mistakes**

- Incorrect handling of arrays containing only 1s or only 0s.
- Not accurately identifying the first 1's position could lead to incorrect count of zeros.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def find_first_one(lst, low, high):
    """ Recursively find the index of the first '1' in the list using binary search. """
    if low > high:
        return high + 1  # This handles the case when there are no '1's in the list.

    mid = (low + high) // 2
    if lst[mid] == 1:
        # Check if it's the first '1' or if the element before it is '0'
        if mid == 0 or lst[mid - 1] == 0:
            return mid
        else:
            return find_first_one(lst, low, mid - 1)
    else:
        return find_first_one(lst, mid + 1, high)

def count_zeros(lst):
    """ Uses the recursive binary search to find the first '1' and calculate the number of '0's. """
    if not lst:
        return 0
    n = len(lst)
    # If thelist has elements, find the first '1'
    first_one_index = find_first_one(lst, 0, n - 1)
    return first_one_index  # The index itself represents the number of '0's since it's zero-indexed
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Test the function with an array [0, 0, 0, 0, 1, 1, 1] to ensure it correctly identifies 4 zeros.
- Check with an array of all ones [1, 1, 1, 1, 1] to confirm that it returns 0.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(log n)` for the binary search.
* **Space Complexity**: `O(log n)` for the recursion stack.
