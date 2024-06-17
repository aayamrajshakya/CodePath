*[[Unit 8 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 10 mins
* 🛠️ **Topics**: Trees, Binary Trees, Recursive Algorithms
    
## 1: U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Question: What is considered the height of a tree?
    - Answer: The height of a tree is the number of edges on the longest path from the root to a leaf. An empty tree has a height of 0.

```
HAPPY CASE
Input: TreeNode(1, TreeNode(2), TreeNode(3))
Output: 2
Explanation: The height from the root to the deepest leaf is 2.

EDGE CASE
Input: None
Output: 0
Explanation: An empty tree has a height of 0.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem falls under tree traversal and depth calculation, common in many applications that require understanding the structure and depth of data hierarchies.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use a recursive function to calculate the maximum depth of the tree.

```
1) If the current node is None, return 0.
2) Recursively calculate the height of the left subtree.
3) Recursively calculate the height of the right subtree.
4) Return the maximum of the two heights plus one for the current node.
```

**⚠️ Common Mistakes**

- Forgetting to add one for the current node, resulting in an undercount of the height.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def height(root):
    """
    Returns the height of the binary tree rooted at `root`.
    Assumes the tree is balanced.
    """
    if root is None:
        return 0  # An empty tree has a height of 0

    # Recursively calculate the height of the left and right subtrees
    left_height = height(root.left)
    right_height = height(root.right)

    # Height of the current node is the greater height of the two subtrees plus 1
    return max(left_height, right_height) + 1
```
    
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Test with various tree configurations, including skewed and balanced trees, to ensure the function returns the correct height.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(n)` where n is the number of nodes in the tree, as the function must visit each node to determine the height.
* **Space Complexity**: `O(h)` for the recursion stack where h is the height of the tree, which could be up to `O(n)` in the worst case of a skewed tree.
