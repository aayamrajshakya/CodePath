*[[Unit 8 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 5 mins
* 🛠️ **Topics**: Trees, Binary Trees, Conditional Checks
    
## 1: U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Question: How should the function behave if one or both child nodes are missing?
    - Answer: The function should return False if either or both child nodes are missing.

```
HAPPY CASE
Input: TreeNode(1, TreeNode(2), TreeNode(2))
Output: True
Explanation: Both children of the root have the same value (2), thus returning True.

EDGE CASE
Input: TreeNode(1, TreeNode(2), None)
Output: False
Explanation: Since one child is missing, the comparison cannot be made, thus returning False.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This is a tree node comparison problem, which is straightforward but critical for understanding tree properties and ensuring data integrity in applications like decision trees.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Check if both children of the root are present and if they have equal values.

```
1) Check if the root and both children nodes are present.
2) If present, compare the values of the left and right children.
3) Return True if they are equal, otherwise return False.
```

**⚠️ Common Mistakes**

- Neglecting to check for the presence of both children, which can lead to errors when attempting to access their values.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def equality(root):
    """
    Check if the root's children in the binary tree have equal value.
    Returns True if both children exist and have the same value, False otherwise.
    """
    if root is None:
        return False  # No root, no children to compare

    if root.left and root.right:
        return root.left.val == root.right.val
    else:
        return False  # One or both children do not exist, cannot have equal values
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Test with various configurations including trees with only one child, no children, and both children to ensure the logic correctly handles each scenario.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(1)` as the operation only involves a couple of condition checks.
* **Space Complexity**: `O(1)` as no additional space is required beyond the input.
