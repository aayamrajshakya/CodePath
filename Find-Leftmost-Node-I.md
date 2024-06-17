*[[Unit 8 Session 1]] (Click for link to problem statements)*

*Looking for the iterative version of this problem?  Go to [[Find Leftmost Node II]]*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 10 mins
* 🛠️ **Topics**: Trees, Binary Trees, Recursion
    
## 1: U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Question: What should the function return if the tree is empty?
    - Answer: The function should return None if the tree is empty.

```
HAPPY CASE
Input: TreeNode(1, TreeNode(2, TreeNode(4)), TreeNode(3))
Output: 4
Explanation: The leftmost node in the tree is the node with value 4.

EDGE CASE
Input: TreeNode(1)
Output: 1
Explanation: The tree has only one node, which is also the leftmost node.
```
 
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem matches a common tree traversal pattern, specifically finding a specific node based on a traversal criterion (leftmost).

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use recursion to find the leftmost node by always following the left child until it no longer exists.

```
1) Start with the root node.
2) If the root node or the left child is not present, return the root's value.
3) Recursively call the function with the left child of the current node until you reach the leftmost node.
```

**⚠️ Common Mistakes**

- Forgetting to check if the root is None before trying to access its value or children.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def left_most(root):
    """
    Return the value of the leftmost node in the binary tree rooted at `root`.
    If the tree is empty, return None.
    """
    if root is None:
        return None
    # If there's no left child, the current node is the leftmost node
    if root.left is None:
        return root.val
    # Recursively continue searching for the leftmost node
    return left_most(root.left)
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Perform a step-by-step verification using test cases, ensuring the function correctly identifies the leftmost node.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(n)` in the worst case where n is the height of the tree, as it depends on the number of nodes to the leftmost leaf.
* **Space Complexity**: `O(1)` if recursion stack space is not considered, as no extra space beyond input is used.
