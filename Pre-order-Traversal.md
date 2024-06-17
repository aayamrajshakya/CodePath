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

- Question: How should the function behave if the tree is empty?
    - Answer: Return an empty list as there are no nodes to traverse in an empty tree.

```
HAPPY CASE
Input: TreeNode(1, TreeNode(2), TreeNode(3))
Output: [1, 2, 3]
Explanation: Preorder traversal visits the node first, then left child, and right child, resulting in the sequence 1, 2, 3.

EDGE CASE
Input: None
Output: []
Explanation: An empty tree results in an empty traversal list.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem is a standard tree traversal problem, specifically a preorder traversal which is fundamental in binary tree operations for processing a node before its children.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Recursively traverse the tree to access each node in the preorder sequence.

```
1) Visit the current node and add its value to the list.
2) Recursively visit the left subtree.
3) Recursively visit the right subtree.
```

**⚠️ Common Mistakes**

- Not maintaining the order of traversal which could lead to incorrect results.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def preorder_helper(current_node, values):
    if not current_node:
        return values
    values.append(current_node.val)  # Visit the node
    preorder_helper(current_node.left, values)  # Traverse the left subtree
    preorder_helper(current_node.right, values)  # Traverse the right subtree
    return values

def preorder_traversal(root):
    values = []
    return preorder_helper(root, values)
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Step through the code with a test tree to ensure that the preorder sequence is correctly assembled from the root through the subtrees.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(n)` where n is the number of nodes in the tree. Each node is visited exactly once during the traversal.
* **Space Complexity**: `O(n)` for the recursion stack in the worst case when the tree is skewed, otherwise `O(log n)` in a balanced tree.
