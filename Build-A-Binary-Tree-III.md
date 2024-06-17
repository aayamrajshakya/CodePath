*[[Unit 8 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 5 mins
* 🛠️ **Topics**: Trees, Binary Trees, Tree Construction
    
## 1: U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem is a basic tree construction challenge, useful for setting up scenarios in more complex tree manipulation tasks.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Create nodes as per the values given and link them as specified to form the tree.

```
1) Create a TreeNode for 'a'.
2) Set 'b' as the left child and 'c' as the right child of 'a'.
3) Set 'd' as the right child of 'c'.
```

**⚠️ Common Mistakes**

- Incorrectly linking nodes or leaving out a node based on the diagram or description.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
root = TreeNode('a')
root.left = TreeNode('b')
root.right = TreeNode('c')
root.right.right = TreeNode('d')
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Verify the tree structure visually or by testing to ensure that all links are correct and that the tree reflects the described structure.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(1)` because the operations to set up the tree are fixed and do not depend on input size.
* **Space Complexity**: `O(1)` for storing a fixed number of nodes.
