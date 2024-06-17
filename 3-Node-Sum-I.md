*[[Unit 8 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 5 mins
* 🛠️ **Topics**: Trees, Binary Trees, Simple Algorithms
    
## 1: U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Question: What are the values of the children nodes and how do they compare to the root?
    - Answer: The values of the children should sum up to the value of the root.

```
HAPPY CASE
Input: TreeNode(5, TreeNode(2), TreeNode(3))
Output: True
Explanation: 2 + 3 = 5, which equals the root's value.

EDGE CASE
Input: TreeNode(5, TreeNode(3), TreeNode(3))
Output: False
Explanation: 3 + 3 = 6, which does not equal the root's value of 5.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This is a simple tree value comparison problem where the solution involves checking a condition involving the root and its immediate children.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Check if the sum of the values of the left and right child nodes equals the value of the root node.

```
1) Check if the root is None (return False if true).
2) Sum the values of root's left and right children.
3) Compare the sum to the root's value.
4) Return True if they match, otherwise return False.
```

**⚠️ Common Mistakes**

- Forgetting to handle the case where the root or any of its children is None, which could lead to attribute errors when trying to access their values.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def check_tree(root):
    return root.val == root.left.val + root.right.val
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Test the function with the happy case and edge case to ensure it behaves as expected.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(1)` because the operation only involves a few comparisons and is independent of the size of the tree.
* **Space Complexity**: `O(1)` because no additional space is required beyond the input.
