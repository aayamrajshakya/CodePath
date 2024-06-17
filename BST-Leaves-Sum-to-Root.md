*[[Unit 8 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 15 mins
* 🛠️ **Topics**: Trees, Binary Trees, Tree Traversal, Summation
    
## 1: U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Question: What should be returned if the tree is empty?
    - Answer: Return False because there are no leaves to compare against the root value.

```
HAPPY CASE
Input: TreeNode(10, TreeNode(5), TreeNode(5))
Output: True
Explanation: The sum of the leaves (5 + 5) equals the value of the root (10).

EDGE CASE
Input: TreeNode(10)
Output: False
Explanation: There is only one node, which is the root, and no leaves to sum, thus it cannot match the root value.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem is a tree traversal problem that involves computing a sum of certain nodes (leaves) and comparing it to a specific node’s value (the root). It involves both traversal and aggregation, common in problems dealing with trees and data structure integrity checks.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Calculate the sum of all leaf node values and compare it to the root node's value.

```
1) Traverse the tree to identify and sum up all leaf nodes.
2) Compare the sum of the leaf nodes to the value of the root node.
3) Return True if they match, otherwise return False.
```

**⚠️ Common Mistakes**

- Not handling edge cases like empty trees or trees with only a root node properly.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def calculate_leaf_sum(node):
    """
    Recursively calculate the sum of all leaf nodes starting from the given node.
    """
    if node is None:
        return 0

    # Check if it's a leaf node (both children are None)
    if node.left is None and node.right is None:
        return node.val

    # Recursively calculate the sum of left and right subtrees
    left_sum = calculate_leaf_sum(node.left)
    right_sum = calculate_leaf_sum(node.right)

    return left_sum + right_sum

def leaf_sum(root):
    """
    Returns `True` if the sum of all leaf node values equals the value of the root node.
    Otherwise, returns `False`.
    """
    if root is None:
        return False

    # Calculate the sum of all leaves using the external helper function
    total_leaf_sum = calculate_leaf_sum(root)

    # Compare the leaf sum to the root's value
    return total_leaf_sum == root.val
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Test the function with a variety of tree structures to ensure it correctly calculates leaf sums and accurately compares them to the root value.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(n)` where n is the number of nodes in the tree as every node needs to be visited to check if it is a leaf.
* **Space Complexity**: `O(h)` where h is the height of the tree, due to the recursion stack depth, which can reach `O(n)` in a highly skewed tree.
