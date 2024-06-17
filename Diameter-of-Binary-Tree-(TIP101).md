*[[Unit 10 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 30 mins
* 🛠️ **Topics**: Tree, Depth-First Search (DFS), Recursion
* 📺 **Non-TIP101 Version**: [[Diameter of Binary Tree]]
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- What should be returned if the tree is empty?
    - 0, since there are no nodes, hence no path exists.

```
HAPPY CASE
Input: root = [1, 2, 3, 4, 5]
Output: 3
Explanation: The diameter of the tree is the path [4, 2, 1, 3] or [5, 2, 1, 3], and both have length 3.

HAPPY CASE
Input: root = [1, 2]
Output: 1
Explanation: The diameter of the tree is the path [2, 1], which has length 1.

EDGE CASE
Input: root = []
Output: 0
Explanation: The tree is empty, so the diameter is 0.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

For Tree problems, we want to consider the following approaches:

- Using Depth-First Search (DFS) to traverse the tree and calculate the height of each node while updating the maximum diameter.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use DFS to traverse the tree. For each node, calculate the height of its left and right subtrees. The diameter at each node is the sum of the heights of its left and right subtrees. Keep track of the maximum diameter encountered during the traversal.

```
1) Define a helper function `dfs(node, max_diameter)` that:
    a) Returns 0 if the node is None.
    b) Recursively calculates the height of the left subtree.
    c) Recursively calculates the height of the right subtree.
    d) Updates the max_diameter with the sum of the left and right subtree heights.
    e) Returns the height of the current node (1 + max of left and right subtree heights).
2) Initialize `max_diameter` to 0.
3) Call the `dfs` function with the root node.
4) Return the value of `max_diameter`.
```

**⚠️ Common Mistakes**

- Forgetting to update the max_diameter during the DFS traversal.
- Not correctly calculating the height of each node.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```
def dfs(node, max_diameter):
    if not node:
        return 0
    
    left_height = dfs(node.left, max_diameter)
    right_height = dfs(node.right, max_diameter)
    
    # Update the diameter
    max_diameter[0] = max(max_diameter[0], left_height + right_height)
    
    # Return the height of the node
    return 1 + max(left_height, right_height)

def diameter(root):
    max_diameter = [0]  # Use a list to hold the max diameter as a mutable reference
    dfs(root, max_diameter)
    return max_diameter[0]
```
 
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with an input to check for the expected output.
- Example: Trace with root = [1, 2, 3, 4, 5]
    - Traverse left subtree, calculate heights
    - Traverse right subtree, calculate heights
    - Update max_diameter as the sum of left and right heights

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

Assume `N` represents the number of nodes in the tree.

* **Time Complexity**: `O(N)` because we need to visit each node once.
* **Space Complexity**: `O(H)` where `H` is the height of the tree, representing the space on the call stack due to recursion.