*[[Unit 9 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 30+ mins
* 🛠️ **Topics**: Tree, Depth-First Search, Recursion
    
## 1: U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Can the tree be empty?
    - Yes, if the tree is empty, return None.

- What should be returned if the tree has only one node and it is either p or q?
    - Return that single node as it is its own ancestor.

```
HAPPY CASE

      3 (root)
     / \
    5   1
   / \ / \
  6  2 0  8
    / \
   7   4

Input: root, p = 5, q = 1
Output: 3
Explanation: The LCA of nodes 5 and 1 is 3.
```
```
EDGE CASE

      3 (root)
     / \
    5   1
   / \ / \
  6  2 0  8
    / \
   7   4

Input: root, p = 5, q = 4
Output: 5
Explanation: The LCA of nodes 5 and 4 is 5 since 5 is an ancestor of 4.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g., Linked List or Dynamic Programming, and strategies or patterns in those categories.

For Tree problems, we want to consider the following approaches:

- Depth-First Search (DFS): Useful for exploring all possible paths to find nodes.
- Recursion: Effective for breaking down the problem into smaller subproblems.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use a DFS approach to traverse the tree. For each node, check if it is either p or q. If so, return that node. Recursively check the left and right subtrees. If both return non-null values, the current node is the LCA.

```
1) If the current node is None, return None.
2) If the current node is either p or q, return the current node.
3) Recursively find LCA in the left and right subtrees.
4) If both left and right are non-null, the current node is the LCA.
5) If only one of the sides is non-null, return that side.
6) Return the result.
```

**⚠️ Common Mistakes**

- Forgetting to handle the case where the tree is empty.
- Not correctly identifying when both left and right subtrees return non-null values.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

def lca(root, p, q):
    if not root:
        return None
    
    # If either p or q is the root, then the root is LCA
    if root == p or root == q:
        return root
    
    # Recursively find LCA in left and right subtrees
    left = lca(root.left, p, q)
    right = lca(root.right, p, q)
    
    # If both left and right are non-null, root is the LCA
    if left and right:
        return root
    
    # If only one of the sides is non-null, return that side
    return left if left else right
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with an input to check for the expected output
- Catch possible edge cases and off-by-one errors
- For a starting point, try checking your code against the Happy/Edge Case(s) above

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

### Time Complexity:
- **O(N)**, where N is the number of nodes in the tree.
- This is because we must visit each node exactly once to determine the LCA.

### Space Complexity:
- **O(N)**, where N is the number of nodes in the tree.
- This is because the recursion stack could hold up to N nodes in the worst case (when the tree is completely unbalanced).