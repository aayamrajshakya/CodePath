*[[Unit 8 Session 1]] (Click for link to problem statements)*

*Looking for the iterative version of this problem?  Go to [[Find Leftmost Path II]]*

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

- Question: What should the function return if the tree is empty?
    - Answer: The function should return an empty list as there is no path to follow.

```
HAPPY CASE
Input: TreeNode('a', TreeNode('b', TreeNode('d'), None), None)
Output: ['a', 'b', 'd']
Explanation: The leftmost path from the root 'a' leads to 'b' and continues to 'd'.

EDGE CASE
Input: TreeNode('a')
Output: ['a']
Explanation: The tree has only one node, so the leftmost path includes just the root node.
```
 
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem fits into tree traversal categories, specifically finding a path in a tree. It involves a recursive depth-first search tailored to always take the leftmost branch until reaching a leaf.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Recursively navigate down the leftmost side of the tree, collecting nodes until a leaf is reached.

```
1) Check if the current node is None. If true, return an empty list.
2) Append the current node’s value to the path list.
3) Recursively call the function for the left child of the current node and add the result to the path list.
4) Return the path list.
```

**⚠️ Common Mistakes**

- Forgetting to handle the case where a node has no left child, which should terminate the recursion.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def left_path(root):
    """
    Recursively collects the values from the leftmost path of the binary tree starting from the given node.
    Returns a list of the collected values.
    """
    if root is None:
        return []
    
    # Recursively collect values from the leftmost path
    return [root.val] + left_path(root.left)
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Validate the code with trees of varying depths and configurations to ensure all possible paths are correctly identified and collected.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(h)` where h is the height of the tree, typically `O(log n)` in a balanced tree but could be `O(n)` in a skewed tree.
* **Space Complexity**: `O(h)` due to the recursion stack, with the worst-case space usage being `O(n)` in a highly skewed tree.
