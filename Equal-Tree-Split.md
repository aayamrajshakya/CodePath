*[[Unit 9 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Hard
* ⏰ **Time to complete**: 30+ mins
* 🛠️ **Topics**: Tree, Depth-First Search, Recursion
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- What should be returned if the tree has only one node?
    - Return False, as one node cannot be split.

```
HAPPY CASE

      1 (root)
     / \
    2   3
   / \ /
  4  5 6

Input: root
Output: True
Explanation: Removing the edge between nodes 1 and 2 can split the tree into two trees with 3 nodes each.
```
```
EDGE CASE

     1 (root)

Input: root
Output: False
Explanation: Only one node cannot be split into equal parts.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

For Tree problems, we want to consider the following approaches:

- Depth-First Search (DFS): Useful for traversing the tree and counting nodes.
- Recursion: Effective for implementing DFS and counting nodes in subtrees.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** First, count the total number of nodes in the tree. Then, perform another DFS to check if any subtree has exactly half the total number of nodes. If such a subtree is found, the tree can be split into two equal parts by removing the edge leading to this subtree.

```
1) Define a helper function `count_nodes(root)` to count the total number of nodes in the tree.
    a) If the current node is None, return 0.
    b) Recursively count nodes in the left and right subtrees and add 1 for the current node.
2) Define another helper function `can_split_helper(root, total_nodes)` to check if any subtree can form half the total number of nodes.
    a) If the current node is None, return 0.
    b) Recursively count nodes in the left and right subtrees.
    c) If any subtree count equals half the total number of nodes, set a flag to True.
    d) Return the total count of nodes for the current subtree.
3) In the main function `can_split(root)`, calculate the total number of nodes.
4) If the total number of nodes is odd, return False.
5) Use the helper function to check if the tree can be split, and return the result.
```

**⚠️ Common Mistakes**

- Forgetting to handle the case where the tree has an odd number of nodes.
- Incorrectly counting nodes in the subtrees.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
class TreeNode:
    def __init__(self, val, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

def count_nodes(root):
    if not root:
        return 0
    return 1 + count_nodes(root.left) + count_nodes(root.right)

def can_split_helper(root, total_nodes):
    if not root:
        return 0
    
    left_count = can_split_helper(root.left, total_nodes)
    right_count = can_split_helper(root.right, total_nodes)
    
    # If any subtree has half of the total nodes, we can split the tree
    if left_count == total_nodes // 2 or right_count == total_nodes // 2:
        can_split_helper.found = True
    
    return 1 + left_count + right_count

def can_split(root):
    total_nodes = count_nodes(root)
    if total_nodes % 2 != 0:
        return False
    
    can_split_helper.found = False
    can_split_helper(root, total_nodes)
    return can_split_helper.found
```
 
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with an input to check for the expected output
- Catch possible edge cases and off-by-one errors
- For a starting point, try checking your code against the Happy/Edge Case(s) above

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

Assume `N` represents the number of nodes in the tree.

* **Time Complexity**: `O(N)` because we need to traverse all the nodes in the tree.
* **Space Complexity**: `O(N)` for the recursion stack in the worst case when the tree is completely unbalanced.