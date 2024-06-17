*[[Unit 10 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 20 mins
* 🛠️ **Topics**: Array, Traversal
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- What should be returned if there is only one building?
    - The index of the single building since it has an ocean view by default.

```
HAPPY CASE
Input: heights = [4, 2, 3, 1]
Output: [0, 2, 3]
Explanation: The buildings at indices 0, 2, and 3 have an ocean view.

HAPPY CASE
Input: heights = [1, 3, 2, 4]
Output: [3]
Explanation: Only the building at index 3 has an ocean view.

EDGE CASE
Input: heights = [1]
Output: [0]
Explanation: The single building has an ocean view by default.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

For Array problems, we want to consider the following approaches:

- Traversing the array from right to left to check for the maximum height seen so far.
- Using a stack to keep track of indices of buildings with ocean views.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Traverse the array from right to left, keeping track of the maximum height seen so far. If the current building is taller than the maximum height, it has an ocean view.

```
1) Initialize `result` as an empty list to store indices of buildings with ocean views.
2) Initialize `max_height` to 0 to keep track of the maximum height seen so far.
3) Traverse the array `heights` from right to left:
    a) If the current building's height is greater than `max_height`:
        i) Append the current index to `result`.
        ii) Update `max_height` to the current building's height.
4) Reverse `result` to get indices in increasing order.
5) Return `result`.
```

**⚠️ Common Mistakes**

- Not correctly traversing the array from right to left.
- Forgetting to reverse the result list to return indices in increasing order.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```
def find_buildings(heights):
    n = len(heights)
    result = []
    max_height = 0
    
    # Traverse from right to left
    for i in range(n - 1, -1, -1):
        if heights[i] > max_height:
            result.append(i)
            max_height = heights[i]
    
    # Reverse the result to get indices in increasing order
    result.reverse()
    return result
```
 
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with an input to check for the expected output.
- Example: Trace with heights = [4, 2, 3, 1]
    - i = 3, max_height = 0, result = [3], max_height = 1
    - i = 2, max_height = 1, result = [3, 2], max_height = 3
    - i = 1, max_height = 3 (skip)
    - i = 0, max_height = 3, result = [3, 2, 0], max_height = 4
    - Reverse result = [0, 2, 3]

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

Assume `N` represents the length of the array `heights`.

* **Time Complexity**: `O(N)` because we need to traverse the array once.
* **Space Complexity**: `O(1)` because we only use a constant amount of extra space.