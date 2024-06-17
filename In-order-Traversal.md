*[[Unit 8 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 10 mins
* 🛠️ **Topics**: Trees, Binary Trees, Tree Traversal
    
## 1: U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Question: What is inorder traversal?
    - Answer: In an inorder traversal of a binary tree, each node is visited in the following order: left child, node itself, then right child.

```
HAPPY CASE
Input: TreeNode(1, TreeNode(2), TreeNode(3))
Output: [2, 1, 3]
Explanation: Inorder traversal visits the left child first, then the node, and finally the right child.

EDGE CASE
Input: TreeNode(1, None, TreeNode(2))
Output: [1, 2]
Explanation: With no left child, the root is visited first, then the right child.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem is a standard tree traversal problem, specifically an inorder traversal which is fundamental in binary tree operations.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Recursively traverse the tree to access each node in the inorder sequence.

```
1) Recursively visit the left subtree.
2) Visit the current node (append its value).
3) Recursively visit the right subtree.
```

**⚠️ Common Mistakes**

- Not maintaining the order of traversal which could lead to incorrect results.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def inorder_helper(current_node, values):
    if not current_node:
        return values
    inorder_helper(current_node.left, values)  # Traverse the left subtree
    values.append(current_node.val)  # Visit the node
    inorder_helper(current_node.right, values)  # Traverse the right subtree
    return values

def inorder_traversal(root):
    values = []
    return inorder_helper(root, values)
```
    
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Step through the code with a test tree to ensure that the inorder sequence is correctly assembled.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(n)` where n is the number of nodes in the tree. Each node is visited exactly once.
* **Space Complexity**: `O(n)` for the recursion stack in the worst case when the tree is skewed.
