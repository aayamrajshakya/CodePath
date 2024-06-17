*[[Unit 10 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 15 mins
* 🛠️ **Topics**: Array, Hashing
* 📺 **Non-TIP101 Version**: [[Contains Duplicates]]
   
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- What should be returned if the array is empty?
    - False, since there are no elements to have duplicates.

```
HAPPY CASE
Input: nums = [1, 2, 3, 1]
Output: True
Explanation: The number 1 appears twice.

HAPPY CASE
Input: nums = [1, 2, 3, 4]
Output: False
Explanation: All numbers are distinct.

EDGE CASE
Input: nums = []
Output: False
Explanation: The array is empty, so no duplicates exist.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

For Array problems, we want to consider the following approaches:

- Using a hash set to track the elements we have seen so far.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use a hash set to keep track of elements we have seen. If an element is found in the set, return True. If we finish the loop without finding any duplicates, return False.

```
1) Initialize an empty set `seen`.
2) Iterate through each element `num` in `nums`:
    a) If `num` is in `seen`, return True.
    b) Otherwise, add `num` to `seen`.
3) If the loop completes without finding duplicates, return False.
```

**⚠️ Common Mistakes**

- Not correctly handling the case where the array is empty.
- Using a data structure with higher time complexity for lookups and insertions.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```
def contains_duplicate(nums):
    seen = set()
    for num in nums:
        if num in seen:
            return True
        seen.add(num)
    return False
```
 
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with an input to check for the expected output.
- Example: Trace with nums = [1, 2, 3, 1]
    - seen = {}
    - seen = {1}
    - seen = {1, 2}
    - seen = {1, 2, 3}
    - 1 in seen, return True

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

Assume `N` represents the length of the array `nums`.

* **Time Complexity**: `O(N)` because we need to iterate through the array once.
* **Space Complexity**: `O(N)` because we need to store the elements we have seen in a set.