*[[Unit 9 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 20+ mins
* 🛠️ **Topics**: Tree, Depth-First Search
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- What should be returned if the tree is empty?
    - Return an empty list.

- Should the list of lonely nodes be in any specific order?
    - No, the list can be in any order.

```
HAPPY CASE

    1 (root)
   / \
  2   3
   \
    4

Input: root
Output: [(4, None, None)]
Explanation: Node 4 is the only lonely node as it is the only child of its parent node 2.
```
```
EDGE CASE

    1 (root)

Input: root
Output: []
Explanation: There are no lonely nodes in a single-node tree.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

For Tree problems, we want to consider the following approaches:

- Depth-First Search (DFS): Useful for traversing the tree and identifying lonely nodes.
- Tree Traversal: Exploring all nodes in the tree to check their children.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use a DFS approach to traverse the tree. During traversal, check if a node has only one child and add the child to the list of lonely nodes.

```
1) Define a helper function `dfs(node, lonely_nodes)` to perform DFS.
    a) If the current node is None, return.
    b) If the node has only a left child, add the left child's value to the list.
    c) If the node has only a right child, add the right child's value to the list.
    d) Recursively call the helper function for the left and right children.
2) In the main function `find_lonely_nodes(root)`, initialize an empty list for lonely nodes.
3) Call the helper function starting from the root node.
4) Return the list of lonely nodes.
```

**⚠️ Common Mistakes**

- Forgetting to handle the case where the tree is empty.
- Incorrectly identifying lonely nodes by not checking both children.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
class TreeNode:
    def __init__(self, val, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

def dfs(node, lonely_nodes):
    if not node:
        return
    
    # Check if the node has only one child and add the child's value to the list
    if node.left and not node.right:
        lonely_nodes.append(node.left.val)
    elif node.right and not node.left:
        lonely_nodes.append(node.right.val)
    
    # Continue DFS on both children
    if node.left:
        dfs(node.left, lonely_nodes)
    if node.right:
        dfs(node.right, lonely_nodes)

def find_lonely_nodes(root):
    lonely_nodes = []
    dfs(root, lonely_nodes)
    return lonely_nodes
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