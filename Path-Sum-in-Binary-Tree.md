*[[Unit 9 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 20+ mins
* 🛠️ **Topics**: Tree, Recursion, Depth-First Search
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Can the tree be empty?
    - Yes, if the tree is empty, return False.

- What should be returned if the tree has only one node?
    - If the node's value equals target_sum, return True; otherwise, return False.

```
HAPPY CASE

        5 (root)
       / \
      4   8
     /   / \
    11  13  4
   / \        \
  7   2        1

Input: root, target_sum = 22
Output: True
Explanation: The path is 5 -> 4 -> 11 -> 2 which sums to 22.
```
```
EDGE CASE

    1 (root)
   / \
  2   3

Input: root, target_sum = 5
Output: False
Explanation: No root-to-leaf path sums to 5.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

For Tree problems, we want to consider the following approaches:

- Depth-First Search (DFS): Useful for traversing the tree and checking path sums.
- Recursion: Effective for exploring different paths in the tree.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use a DFS approach to traverse the tree. At each node, check if it's a leaf node and if the path sum equals the target_sum. Recursively check the left and right subtrees with the updated target_sum.

```
1) Base case: If the current node is None, return False.
2) Check if the current node is a leaf (no children) and if its value equals target_sum.
3) Recursively check the left and right subtrees with the updated target_sum (subtract the current node's value from target_sum).
4) Return True if either subtree has a valid path, otherwise return False.
```

**⚠️ Common Mistakes**

- Forgetting to handle cases where the tree is empty.
- Not correctly updating the target_sum for recursive calls.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

def has_path_sum(root, target_sum):
    if not root:
        return False

    # Check if we're at a leaf node and the path sum equals the target sum
    if not root.left and not root.right:
        return root.val == target_sum

    # Recursively check the left and right subtree with the updated target sum
    return (has_path_sum(root.left, target_sum - root.val) or 
            has_path_sum(root.right, target_sum - root.val))
```
 
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with an input to check for the expected output
- Catch possible edge cases and off-by-one errors
- For a starting point, try checking your code against the Happy/Edge Case(s) above

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

Assume `N` represents the number of nodes in the tree.

* **Time Complexity**: `O(N)` because we may need to traverse all the nodes in the tree.
* **Space Complexity**: `O(N)` for the recursion stack in the worst case when the tree is completely unbalanced.