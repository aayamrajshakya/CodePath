*[[Unit 8 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 10 mins
* 🛠️ **Topics**: Trees, Binary Trees, Minimum Value Search
    
## 1: U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Question: What should be returned if the tree is empty?
    - Answer: Return None, as there is no minimum value in an empty tree.

```
HAPPY CASE
Input: TreeNode(4, TreeNode(2, TreeNode(1), TreeNode(3)), TreeNode(6))
Output: 1
Explanation: The minimum value in the tree is 1.

EDGE CASE
Input: None
Output: None
Explanation: No values exist in an empty tree.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem is a fundamental tree traversal challenge where the goal is to find the minimum value. It's a common operation used in scenarios involving optimizations, comparisons, or condition checks within tree-based data structures.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Traverse the tree using a recursive depth-first search to find the lowest value.

```
1) If the current node is None, return a very large number (to ensure it's not considered as the minimum).
2) Recursively find the minimum value in both the left and right subtrees.
3) Return the minimum of the current node’s value and the minimum values from both subtrees.
```

**⚠️ Common Mistakes**

- Returning None instead of a numeric maximum when a node is null, which could complicate comparison logic.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def tree_min(node):
    """
    Returns the node with the least value in the binary tree rooted at `node`.
    If the tree is empty, return None.
    """
    if node is None:
        return float('inf')  # Treat empty node as maximum possible value

    # Recursively find the min in the left and right subtree
    left_min = tree_min(node.left)
    right_min = tree_min(node.right)

    # Return the minimum value found
    return min(node.val, left_min, right_min)
```
   
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Test the function with trees of varying sizes and shapes, including extremely unbalanced trees, to confirm accurate minimum value identification.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(n)` where n is the number of nodes in the tree, as each node's value needs to be checked.
* **Space Complexity**: `O(h)` where h is the height of the tree due to the recursion stack, potentially reaching `O(n)` in a highly skewed tree.
