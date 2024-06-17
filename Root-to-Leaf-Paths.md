*[[Unit 9 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 30+ mins
* 🛠️ **Topics**: Tree, Depth-First Search
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- What should we return if the root is None?
    - Return an empty list.

- Should the paths be returned in any specific order?
    - No, any order is acceptable.

```
HAPPY CASE

    1 (root)
   / \
  2   3
   \
    5

Input: root
Output: ["1->2->5", "1->3"]
Explanation: There are two root-to-leaf paths in the given tree.
```
```
EDGE CASE

    None (root)

Input: root
Output: []
Explanation: The tree is empty, so no paths exist.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

For Tree problems, we want to consider the following approaches:

- Depth-First Search (DFS): We can use DFS to explore all paths from the root to the leaf nodes.
- Backtracking: We can use backtracking to build the path as we traverse the tree.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** We will use a Depth-First Search (DFS) approach to explore all the paths from the root to the leaf nodes. During the traversal, we will build the path and store it when we reach a leaf node.

```
1) Initialize an empty list to store all the paths.
2) Define a helper function `dfs(node, path, paths)` to perform DFS.
    a) If the current node is None, return.
    b) Append the current node's value to the path.
    c) If the current node is a leaf, add the current path to the list of paths.
    d) Otherwise, recursively call the helper function for the left and right children.
3) Call the helper function starting from the root node.
4) Return the list of paths.
```

**⚠️ Common Mistakes**

- Forgetting to check for None nodes.
- Not handling the case when the root is None.
- Incorrectly building the path string.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def dfs(node, path, paths):
    if not node:
        return
    
    # Append current node value to path
    if path:
        path += ""->"" + str(node.val)
    else:
        path = str(node.val)
    
    # Check if it's a leaf node
    if not node.left and not node.right:
        paths.append(path)
    else:
        # Continue to explore the left and right subtree
        dfs(node.left, path, paths)
        dfs(node.right, path, paths)

def binary_tree_paths(root):
    paths = []
    dfs(root, """", paths)
    return paths
```
 
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with an input to check for the expected output
- Catch possible edge cases and off-by-one errors
- For a starting point, try checking your code against the Happy/Edge Case(s) above

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

Assume `N` represents the number of nodes in the binary tree.

* **Time Complexity**: `O(N)` because we need to traverse all the nodes in the tree.
* **Space Complexity**: `O(N)` for the recursion stack in the worst case when the tree is completely unbalanced.