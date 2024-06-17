*[[Unit 9 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 30+ mins
* 🛠️ **Topics**: Tree, Recursion, Boolean Logic
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Can non-leaf nodes have other values apart from "AND" or "OR"?
    - No, non-leaf nodes only have "AND" or "OR" as values.

- What should be returned if the tree is empty?
    - The problem guarantees a non-empty full binary tree, so this case is not applicable.

```
HAPPY CASE 1

      AND (root)
     /   \
    OR    AND
   / \    / \
  T   F  T   T

Input: root
Output: True
Explanation: The evaluation proceeds as follows:
- Evaluate left subtree [OR, True, False] -> True OR False = True
- Evaluate right subtree [AND, True, True] -> True AND True = True
- Apply root operation: True AND True = True
```
```
HAPPY CASE 2

      OR (root)
     /  \
   AND   OR
   / \   / \
  F   F F   F

Input: root
Output: False
Explanation: The evaluation proceeds as follows:
- Evaluate left subtree [AND, False, False] -> False AND False = False
- Evaluate right subtree [OR, False, False] -> False OR False = False
- Apply root operation: False OR False = False
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

For Tree problems, we want to consider the following approaches:

- Recursion: Useful for evaluating the tree structure.
- Divide and Conquer: Evaluate left and right subtrees separately and combine their results.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use a recursive approach to evaluate the tree. For each node, evaluate its left and right children, then apply the node's boolean operation to the results of the children.

```
1) Base case: If the node is a leaf (no children), return its boolean value.
2) Recursive case: Evaluate the left and right children.
3) Apply the boolean operation of the current node to the results of the left and right children.
4) Return the result.
```

**⚠️ Common Mistakes**

- Forgetting to handle non-leaf nodes properly.
- Not correctly applying the boolean operations.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
class TreeNode:
    def __init__(self, val, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

def evaluate_tree(root):
    # Base case: if the node is a leaf, return its boolean value
    if not root.left and not root.right:
        return root.val  # Since it's a leaf, root.val is True or False
    
    # Recursive case: Evaluate left and right children
    left_val = evaluate_tree(root.left)
    right_val = evaluate_tree(root.right)
    
    # Apply the boolean operation
    if root.val == 'AND':
        return left_val and right_val
    elif root.val == 'OR':
        return left_val or right_val
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