*[[Unit 8 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 15 mins
* 🛠️ **Topics**: Trees, Binary Search Trees, Algorithms
    
## 1: U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Question: What defines a "full tree"?
    - Answer: A binary tree is full if every node has either zero or two children, not one.

```
HAPPY CASE
Input: TreeNode(10, TreeNode(5, TreeNode(3), TreeNode(7)), TreeNode(15, None, TreeNode(20)))
Output: False
Explanation: The node with value 15 has only one child, thus the tree is not full.

EDGE CASE
Input: TreeNode(10, TreeNode(5), None)
Output: False
Explanation: The root node has only one child, making it not a full tree.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem is a tree property validation problem, typically requiring a traversal to check each node's children compliance with the full tree definition.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Traverse the tree and verify that every node either has zero or two children.

```
1) If the current node is None, return True (a trivially full subtree).
2) If the current node has exactly one child, return False.
3) Recursively check the left and right children to confirm both are either full or empty.
4) Return True only if both subtrees of every node are full, based on the recursive checks.
```

**⚠️ Common Mistakes**

- Incorrectly returning True for nodes that have only one child.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def is_full_tree(root):
    """
    Determine if the binary tree rooted at `root` is a full binary tree.
    A full binary tree is defined as a tree in which every node has either 0 or 2 children.
    """
    if root is None:
        return True
    
    # Check the children count:
    # If both left and right are None, it's a leaf node, thus a full subtree at this node.
    # If both left and right are not None, we need to check recursively that both subtrees are full.
    if root.left is None and root.right is None:
        return True
    if root.left is not None and root.right is not None:
        return is_full_tree(root.left) and is_full_tree(root.right)
    
    # If one child is None and the other is not, it's not a full tree.
    return False
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Validate with different tree structures including balanced, skewed, and minimal trees to ensure all tree types are correctly evaluated.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(n)` where n is the number of nodes in the tree. The algorithm needs to visit each node to check its children's status.
* **Space Complexity**: `O(h)` where h is the height of the tree, due to the recursion stack depth. This can reach `O(n)` in a skewed tree.
