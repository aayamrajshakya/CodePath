*[[Unit 8 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 5 mins
* 🛠️ **Topics**: Trees, Binary Trees
    
## 1: U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This is a basic tree construction problem, typically used as a foundation for more complex tree manipulations or traversals.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Create nodes and assign them as children to form the specified binary tree structure.

```
1) Create the root node with value 5.
2) Create a left child node with value 10 and assign to root.
3) Create a right child node with value 20 and assign to root.
```

**⚠️ Common Mistakes**

- Incorrect assignment of children, which could lead to an incorrect tree structure.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
root = TreeNode(5)
root.left = TreeNode(10)
root.right = TreeNode(20)
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Check the structure of the tree to ensure that nodes are connected as expected.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(1)` because the creation and connection of nodes are fixed and do not depend on any input size.
* **Space Complexity**: `O(1)` because a constant amount of space is used irrespective of input.
