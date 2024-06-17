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
    - Yes, if the tree is empty, return 0.

- What should be returned if the tree has only one node?
    - The diameter of a single node tree is 0.

```
HAPPY CASE
 
      1 (root)
     / \
    2   3
   / \
  4   5

Input: root
Output: 3
Explanation: The longest path is [4, 2, 1, 3] or [5, 2, 1, 3], and the length is 3 edges.
```
```
EDGE CASE

    1 (root)

Input: root
Output: 0
Explanation: The tree has only one node, so the diameter is 0.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g., Linked List or Dynamic Programming, and strategies or patterns in those categories.

For Tree problems, we want to consider the following approaches:

- Depth-First Search (DFS): Useful for calculating the height and updating the diameter.
- Recursion: Effective for traversing and updating the tree.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use a DFS approach to traverse the tree. For each node, calculate the height of its left and right subtrees, update the diameter, and return the height of the node.

```
1) Define a helper function `dfs(node, max_diameter)` to calculate the height and update the diameter.
    a) If the current node is None, return 0.
    b) Recursively calculate the height of the left subtree.
    c) Recursively calculate the height of the right subtree.
    d) Update the diameter as the maximum of the current diameter and the sum of left and right subtree heights.
    e) Return the height of the node as 1 plus the maximum of left and right subtree heights.
2) In the main function `diameter(root)`, initialize max_diameter to 0.
3) Call the helper function to start the DFS from the root.
4) Return the maximum diameter.
```

**⚠️ Common Mistakes**

- Forgetting to handle the case where the tree is empty.
- Not correctly updating the diameter for each node.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

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

- Trace through your code with an input to check for the expected output
- Catch possible edge cases and off-by-one errors
- For a starting point, try checking your code against the Happy/Edge Case(s) above

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

### Time Complexity:
- **O(N)**, where N is the number of nodes in the tree.
- This is because we must visit each node exactly once to calculate heights and update the diameter.

### Space Complexity:
- **O(N)**, where N is the number of nodes in the tree.
- This is because the recursion stack could hold up to N nodes in the worst case (when the tree is completely unbalanced).