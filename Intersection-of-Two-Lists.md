*[[Unit 10 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 15 mins
* 🛠️ **Topics**: Set, Array

## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- What should be returned if either `nums1` or `nums2` is empty?
    - An empty list `[]`, since there would be no intersection.

```
HAPPY CASE
Input: nums1 = [1, 2, 2, 1], nums2 = [2, 2]
Output: [2]
Explanation: The intersection of the lists is [2].

HAPPY CASE
Input: nums1 = [4, 9, 5], nums2 = [9, 4, 9, 8, 4]
Output: [9, 4]
Explanation: The intersection of the lists is [9, 4]. The order does not matter.

EDGE CASE
Input: nums1 = [], nums2 = [1, 2, 3]
Output: []
Explanation: One of the lists is empty, so the intersection is an empty list.

EDGE CASE
Input: nums1 = [1, 2, 3], nums2 = []
Output: []
Explanation: One of the lists is empty, so the intersection is an empty list.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

For Array and Set problems, we want to consider the following approaches:

- Using set operations to find the intersection of the two lists.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Convert both lists to sets to remove duplicates and allow for set operations. Find the intersection of the two sets and return the result as a list.

```
1) Convert both `nums1` and `nums2` to sets, `set1` and `set2`, to remove duplicates.
2) Find the intersection of `set1` and `set2`.
3) Convert the intersection set back to a list.
4) Return the list.
```

**⚠️ Common Mistakes**

- Not correctly handling the case where one or both lists are empty.
- Forgetting to remove duplicates before finding the intersection.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```
def intersection(nums1, nums2):
    # Convert both lists to sets to remove duplicates and allow for set operations
    set1 = set(nums1)
    set2 = set(nums2)
    
    # Find the intersection of the two sets
    intersection_set = set1 & set2
    
    # Convert the set back to a list and return it
    return list(intersection_set)
```
 
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with an input to check for the expected output.
- Example: Trace with nums1 = [1, 2, 2, 1], nums2 = [2, 2]
    - set1 = {1, 2}
    - set2 = {2}
    - intersection_set = {2}
    - Return [2]

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

Assume `N` and `M` represent the lengths of the arrays `nums1` and `nums2` respectively.

* **Time Complexity**: `O(N + M)` because we need to traverse both arrays to create the sets.
* **Space Complexity**: `O(N + M)` because we need to store the elements of both arrays in sets.