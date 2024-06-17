*[[Unit 8 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 15 mins
* 🛠️ **Topics**: Trees, Binary Search Trees, Tree Traversal, Sorting
    
## 1: U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Question: What if the tree is empty?
    - Answer: Return an empty list as there are no leaves to collect.

```
HAPPY CASE
Input: TreeNode(10, TreeNode(5), TreeNode(15, None, TreeNode(20)))
Output: [20, 5]
Explanation: The leaves are the nodes with values 5 and 20, and they are listed in descending order.

EDGE CASE
Input: TreeNode(10)
Output: [10]
Explanation: The single node is both a root and a leaf.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This is a leaf collection problem that involves tree traversal and sorting. The strategy aligns with post-order traversal to ensure all leaves are accessed before sorting.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Traverse the tree to collect leaf nodes, then sort the collected values in descending order.

```
1) Define a helper function to traverse the tree and collect leaf values.
2) Start from the root and traverse to the right subtree first to facilitate descending order collection.
3) Check each node to determine if it is a leaf (i.e., no left or right children).
4) Store leaf values.
5) After traversal, the leaves collected from right to left are already in descending order.
```

**⚠️ Common Mistakes**

- Not correctly identifying leaf nodes, especially in edge cases with single nodes or unbalanced trees.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def collect_leaves_descending(root, leaves):
    """
    Helper function to collect leaf nodes' values from the BST rooted at `root` in descending order.
    The values are collected directly into the list `leaves`.
    """
    if root is None:
        return

    # First, visit the right child (to ensure descending order)
    collect_leaves_descending(root.right, leaves)

    # Check if it's a leaf node
    if root.left is None and root.right is None:
        leaves.append(root.val)

    # Then, visit the left child
    collect_leaves_descending(root.left, leaves)

def descending_leaves(root):
    """
    Return a list of leaf values in descending order from the BST rooted at `root`.
    """
    leaves = []
    collect_leaves_descending(root, leaves)
    return leaves
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Execute with a variety of test cases to ensure the leaf values are accurately collected and appropriately sorted in descending order without requiring additional sorting steps.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(n)` where n is the number of nodes in the tree. Each node is visited once.
* **Space Complexity**: `O(h)` where h is the height of the tree due to recursion, which can be up to `O(n)` in unbalanced trees but is typically `O(log n)` in balanced trees.
