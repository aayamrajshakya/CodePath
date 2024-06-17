*[[Unit 8 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 10 mins
* 🛠️ **Topics**: Trees, Binary Trees, Max Value Search
    
## 1: U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Question: What should be returned if the tree is empty?
    - Answer: Return None, as there is no maximum value in an empty tree.

```
HAPPY CASE
Input: TreeNode(3, TreeNode(1), TreeNode(5, TreeNode(4), TreeNode(6)))
Output: 6
Explanation: The maximum value in the tree is 6.

EDGE CASE
Input: None
Output: None
Explanation: No values exist in an empty tree.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem is a fundamental tree traversal challenge where the goal is to find the maximum value. It's a common operation used in scenarios where data integrity and maximum values need to be checked, like in priority-based systems or analytics.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Traverse the tree to find the highest value using a recursive depth-first search.

```
1) If the current node is None, return a very small number (to ensure it's not considered as the max).
2) Recursively find the maximum value in both the left and right subtrees.
3) Return the maximum of the current node’s value and the maximum values from both subtrees.
```

**⚠️ Common Mistakes**

- Returning None instead of a numeric minimum when a node is null, which could complicate comparison logic.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def tree_max(node):
    """
    Returns the node with the greatest value in the binary tree rooted at `node`.
    If the tree is empty, return None.
    """
    if node is None:
        return float('-inf')  # Treat empty node as minimum possible value

    # Recursively find the max in the left and right subtree
    left_max = tree_max(node.left)
    right_max = tree_max(node.right)

    # Return the maximum value found
    return max(node.val, left_max, right_max)
```
    
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Test the function with trees of varying sizes and shapes, including extremely unbalanced trees, to confirm accurate maximum value identification.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(n)` where n is the number of nodes in the tree, as each node's value needs to be checked.
* **Space Complexity**: `O(h)` where h is the height of the tree due to the recursion stack, potentially reaching `O(n)` in a highly skewed tree.
