*[[Unit 9 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 20+ mins
* 🛠️ **Topics**: Binary Trees, Tree Traversal, Recursion
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Can the tree be empty?
    - Yes, if the tree is empty, return True.
- What if one subtree is None while the other is not?
    - Return False as the tree is not symmetric.
- How do we handle leaf nodes?
    - Leaf nodes are symmetric as they have no children.

```
HAPPY CASE 1

    1 (root)
   / \
  2   2

Input: root
Output: True
Explanation: The left and right subtrees are mirrors of each other.
```

```
HAPPY CASE 2

      1 (root)
     / \
    2   2
   / \ / \
  3  4 4  3

Input: root
Output: True
Explanation: The left and right subtrees are mirrors of each other.
```
```
EDGE CASE

      1 (root)
     / \
    2   2
   /   / \
  3   3   4

Input: root
Output: False
Explanation: The left and right subtrees are not mirrors of each other.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

For Tree problems, we want to consider the following approaches:

- Depth-First Search (DFS)
- Breadth-First Search (BFS)
- Recursive approach to compare subtrees

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use a helper function to recursively compare the left and right subtrees to determine if they are mirrors.

```
1) If both left and right nodes are None, return True.
2) If only one of the nodes is None, return False.
3) If the values of the left and right nodes do not match, return False.
4) Recursively compare the left child of the left node with the right child of the right node, and the right child of the left node with the left child of the right node.
5) Return the result of the recursive comparisons.
```

**⚠️ Common Mistakes**

- Forgetting to check if the nodes are None before accessing their values.
- Not properly handling the base cases in the recursive function.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
class TreeNode:
    def __init__(self, val, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

def is_mirror(left, right):
    if not left and not right:
        return True  # Both are None, hence symmetric
    if not left or not right:
        return False  # Only one is None, hence not symmetric
    if left.val != right.val:
        return False  # Values do not match, hence not symmetric
    # Recursively check the outer pairs and the inner pairs for symmetry
    return is_mirror(left.left, right.right) and is_mirror(left.right, right.left)

def is_symmetric(root):
    if not root:
        return True  # An empty tree is symmetric.
    return is_mirror(root.left, root.right)
```
 
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with an input to check for the expected output
- Catch possible edge cases and off-by-one errors
- For a starting point, try checking your code against the Happy/Edge Case(s) above

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

Assume `N` represents the number of nodes in the binary tree.

* **Time Complexity**: `O(N)` because we need to check all nodes in the tree.
* **Space Complexity**: `O(N)` due to the recursive stack space in the worst case.