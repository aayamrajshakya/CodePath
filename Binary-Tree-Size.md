*[[Unit 8 Session 1]] (Click for link to problem statements)*

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

- Question: How does the function handle an empty tree?
    - Answer: The function should return 0 for an empty tree as there are no nodes to count.

```
HAPPY CASE
Input: TreeNode(1, TreeNode(2), TreeNode(3))
Output: 3
Explanation: There are three nodes in the tree.

EDGE CASE
Input: None
Output: 0
Explanation: There are no nodes in an empty tree.
```
  
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem aligns with tree traversal techniques, particularly depth-first search, used to count nodes in a binary tree.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use recursion to traverse the tree and count nodes.

```
1) If the current node is None, return 0.
2) Recursively count the nodes in the left subtree.
3) Recursively count the nodes in the right subtree.
4) Add the counts from step 2 and 3, plus one for the current node.
```

**⚠️ Common Mistakes**

- Forgetting to add one for the current node, which leads to an undercount.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def size(root):
    """
    Calculate the number of nodes in the binary tree rooted at `root`.
    """
    if root is None:
        return 0
    return 1 + size(root.left) + size(root.right)
```
    
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Test the function with a few different tree configurations to ensure accuracy across various tree sizes and shapes.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(n)` where n is the number of nodes in the tree. Each node is visited exactly once during the traversal.
* **Space Complexity**: `O(h)` where h is the height of the tree, due to the recursion stack. This is O(n) in the worst case for a skewed tree.
