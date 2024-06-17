*[[Unit 8 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 10 mins
* 🛠️ **Topics**: Trees, Binary Trees, Search Algorithms
    
## 1: U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Question: How to handle a tree with duplicate values?
    - Answer: The problem states that all nodes have unique values, so this scenario does not apply.

```
HAPPY CASE
Input: TreeNode(10, TreeNode(5, TreeNode(2), TreeNode(7)), TreeNode(15)), value = 7
Output: True
Explanation: The node with value 7 is a leaf node (nodes 2 and 7 are leaves, 7 is checked).

EDGE CASE
Input: TreeNode(10, TreeNode(5), None), value = 5
Output: False
Explanation: Node 5 is not a leaf because it has a child.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This is a targeted search problem where the goal is to identify whether a node with a given value is a leaf in the tree. It involves a traversal with a condition check.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Traverse the tree to find a node with the specified value and check if it is a leaf (no children).

```
1) If the tree is empty (root is None), return False.
2) If the current node's value matches the target, check if it has no children.
3) If it matches and is a leaf, return True.
4) Otherwise, recursively search in the left and right subtrees.
```

**⚠️ Common Mistakes**

- Incorrectly identifying a node as a leaf when it has one or more children.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def is_leaf(root, value):
    """
    Search the entire binary tree rooted at `root` for a node with the specified `value`
    and check if it is a leaf. A leaf node is a node that has no children.
    """
    if root is None:
        return False  # Node not found, so it's not a leaf

    # If the current node's value matches the search value, check if it's a leaf
    if root.val == value:
        return root.left is None and root.right is None

    # Search in the left and right subtrees
    return is_leaf(root.left, value) or is_leaf(root.right, value)
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Test with trees where the target node varies in position (root, middle, leaf) to ensure robustness in identifying leaf status.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(n)` where n is the number of nodes in the tree, as the worst case requires visiting every node.
* **Space Complexity**: `O(h)` where h is the height of the tree, due to recursion. This could be `O(n)` in a skewed tree.
