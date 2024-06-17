*[[Unit 8 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 10 mins
* 🛠️ **Topics**: Trees, Binary Search Trees, Search Algorithms
    
## 1: U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Question: What if the value is not found in any node?
    - Answer: Return False if the value is not found in any node in the tree.

```
HAPPY CASE
Input: TreeNode(10, TreeNode(5), TreeNode(15, None, TreeNode(20))), value = 20
Output: True
Explanation: The node with value 20 is a leaf node (no children) in the tree.

EDGE CASE
Input: TreeNode(10, TreeNode(5), None), value = 5
Output: False
Explanation: Node 5 is not a leaf because it has a left child.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This is a search problem in a binary search tree, utilizing the BST properties to efficiently determine if a node is a leaf.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use the binary search tree properties to find the node and check if it is a leaf.

```
1) If the tree is empty (root is None), return False.
2) If the node’s value equals the target value, check if both children are None.
3) If the value is less than the node’s value, search the left subtree.
4) If the value is more than the node’s value, search the right subtree.
```

**⚠️ Common Mistakes**

- Not using the BST properties to minimize the search path, resulting in unnecessary checks.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def is_leaf_bst(root, value):
    """
    Search for a node with the given `value` in the binary search tree rooted at `root`
    and check if it is a leaf. A leaf is a node with no children.
    """
    if root is None:
        return False  # Node not found, so it's not a leaf

    if root.val == value:
        return root.left is None and root.right is None  # Check if the node is a leaf

    # Recursive search in the left and right subtrees
    elif value < root.val:
        return is_leaf_bst(root.left, value)
    else:
        return is_leaf_bst(root.right, value)
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Perform functional testing to verify that the leaf check and binary search work correctly across a range of test cases, including edge cases with minimal or unbalanced trees.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(log n)` on average, where n is the number of nodes in the tree. The height of the tree, due to its balanced nature, allows for log-scale depth traversal.
* **Space Complexity**: `O(log n)` due to the recursion depth, which is the height of the tree in the balanced case.
