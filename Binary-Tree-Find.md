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

- Question: What if the tree is empty?
    - Answer: Return False if the tree is empty as there are no nodes to find.

```
HAPPY CASE
Input: TreeNode(10, TreeNode(5), TreeNode(15)), value = 5
Output: True
Explanation: The value 5 is found in the tree.

EDGE CASE
Input: None, value = 5
Output: False
Explanation: An empty tree cannot contain any value.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem involves a tree search, commonly tackled with either depth-first search (DFS) or breadth-first search (BFS). Given the structure, DFS is a natural fit.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Traverse the tree using a recursive depth-first search to find the node with the given value.

```
1) Start at the root.
2) If the current node is None, return False.
3) If the current node's value matches the target, return True.
4) Recursively search the left subtree.
5) If not found in the left, recursively search the right subtree.
```

**⚠️ Common Mistakes**

- Not considering that the node might not exist in the tree.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def find(root, value):
    """
    Search for a node with the given `value` in the binary tree rooted at `root`.
    Return True if the value is found, otherwise return False.
    """
    if root is None:
        return False
    if root.val == value:
        return True
    return find(root.left, value) or find(root.right, value)
```
    
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Validate the function with trees of varying shapes and sizes to ensure all paths and conditions are covered.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(n)` where n is the number of nodes in the tree. In the worst case, we might need to visit every node.
* **Space Complexity**: `O(h)` where h is the height of the tree, due to the recursion stack. This is O(n) in the worst case for a skewed tree.
