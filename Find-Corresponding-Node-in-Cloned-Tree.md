*[[Unit 9 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 30+ mins
* 🛠️ **Topics**: Tree, Depth-First Search, Tree Traversal
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Can the target node be null?
    - No, the target node is always a valid reference in the original tree.

- What should be returned if the trees are empty?
    - The problem guarantees non-empty trees, so this case is not applicable.

```
HAPPY CASE
 
    7 (root)    7 (clone_root)
   / \         / \
  4   3       4   3
     / \     / \
    6  19   6  19

Input: root, clone_root, target = 3
Output: Reference to the node with value 3 in the cloned tree.
Explanation: The target node with value 3 in the original tree should correspond to the node with value 3 in the cloned tree.
```
```
EDGE CASE

   1 (root)    1 (clone_root) 

Input: root, clone_root, 1
Output: Reference to the node with value 1 in the cloned tree.
Explanation: There is only one node in the tree, so it must be the target node.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

For Tree problems, we want to consider the following approaches:

- Depth-First Search (DFS): Useful for traversing the tree and locating the target node.
- Tree Traversal: Exploring nodes to find the reference in the cloned tree.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use a DFS approach to simultaneously traverse both the original and cloned trees. When the target node is found in the original tree, return the corresponding node from the cloned tree.

```
1) Define a helper function `dfs(node_o, node_c, target)` to perform DFS.
    a) If the current node in the original tree is None, return None.
    b) If the current node in the original tree is the target, return the corresponding node in the cloned tree.
    c) Recursively search in the left subtree.
    d) If the target is found in the left subtree, return the result.
    e) Otherwise, recursively search in the right subtree and return the result.
2) In the main function `get_target_copy(original, cloned, target)`, call the helper function to start the DFS from the root nodes.
3) Return the result of the helper function.
```

**⚠️ Common Mistakes**

- Forgetting to handle cases where the target is deep in the tree.
- Not correctly mapping the corresponding nodes between the original and cloned trees.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
class TreeNode:
    def __init__(self, val, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

def dfs(node_o, node_c, target):
    if not node_o:
        return None
    
    # Check if the current node in the original tree is the target
    if node_o == target:
        return node_c
    
    # Recursively search in the left subtree
    left_result = dfs(node_o.left, node_c.left, target)
    if left_result:
        return left_result
    
    # Recursively search in the right subtree
    return dfs(node_o.right, node_c.right, target)

def get_target_copy(original, cloned, target):
    return dfs(original, cloned, target)
```
 
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with an input to check for the expected output
- Catch possible edge cases and off-by-one errors
- For a starting point, try checking your code against the Happy/Edge Case(s) above

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

Assume `N` represents the number of nodes in the trees.

* **Time Complexity**: `O(N)` because we may need to traverse all the nodes in the tree.
* **Space Complexity**: `O(N)` for the recursion stack in the worst case when the tree is completely unbalanced.