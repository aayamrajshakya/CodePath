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

- Question: How does the balanced nature of the tree affect the search?
    - Answer: A balanced tree ensures that the height is minimal, allowing for more efficient searches compared to an unbalanced tree.

```
HAPPY CASE
Input: TreeNode(10, TreeNode(5), TreeNode(15)), value = 15
Output: True
Explanation: The value 15 is found in the right subtree of the root.

EDGE CASE
Input: TreeNode(10, TreeNode(5), TreeNode(15)), value = 20
Output: False
Explanation: The value 20 is not found in the tree.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This is a binary search tree (BST) search problem, which typically utilizes the BST property to efficiently find a node.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Utilize the properties of a binary search tree to efficiently find the node.

```
1) Start at the root.
2) If the current node is None, return False.
3) If the current node's value matches the target, return True.
4) If the target value is less than the current node's value, search the left subtree.
5) Otherwise, search the right subtree.
```

**⚠️ Common Mistakes**

- Forgetting to utilize the BST property that left child values are less and right child values are greater than the current node, which can lead to inefficient searches.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def find_bst(root, value):
    """
    Search for a node with the given `value` in the binary search tree rooted at `root`.
    Return True if the value is found, otherwise return False.
    """
    if root is None:
        return False
    if root.val == value:
        return True
    elif value < root.val:
        return find_bst(root.left, value)
    else:
        return find_bst(root.right, value)
```
    
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Test with various tree structures and values to ensure the search algorithm efficiently utilizes the BST properties.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(log n)` on average, where n is the number of nodes in the tree. The height of the tree, due to its balanced nature, allows for log-scale depth traversal.
* **Space Complexity**: `O(log n)` due to the recursion depth, which is the height of the tree in the balanced case.
