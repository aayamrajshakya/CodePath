*[[Unit 9 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 20+ mins
* 🛠️ **Topics**: Tree, Recursion, Arithmetic Operations
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- What should be returned if the tree is empty?
    - The problem guarantees a non-empty full binary tree, so this case is not applicable.

- How should division by zero be handled?
    - This problem assumes the inputs will not lead to division by zero.

```
HAPPY CASE

      * (root)
     / \
    +   *
   / \ / \
  3  2 4  5

Input: root
Output: 50
Explanation: The evaluation proceeds as follows:
- Evaluate left subtree [+ 3 2] -> 3 + 2 = 5
- Evaluate right subtree [* 4 5] -> 4 * 5 = 20
- Apply root operation: 5 * 20 = 100
```
```
EDGE CASE

    + (root)
   / \
  -   *
 / \ / \
10 5 2 3

Input: root
Output: 11
Explanation: The evaluation proceeds as follows:
- Evaluate left subtree [- 10 5] -> 10 - 5 = 5
- Evaluate right subtree [* 2 3] -> 2 * 3 = 6
- Apply root operation: 5 + 6 = 11
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

For Tree problems, we want to consider the following approaches:

- Recursion: Useful for evaluating nodes and their children.
- Divide and Conquer: Evaluate left and right subtrees and combine their results.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use a recursive approach to evaluate the tree. For each node, if it is a leaf node, return its value. Otherwise, evaluate its left and right children and apply the node's operation.

```
1) Base case: If the node is a leaf (no children), return its integer value.
2) Recursive case: Evaluate the left and right children.
3) Apply the operation of the current node to the results of the left and right children.
4) Return the result.
```

**⚠️ Common Mistakes**

- Forgetting to handle different arithmetic operations correctly.
- Not correctly evaluating leaf nodes and non-leaf nodes.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
class TreeNode:
    def __init__(self, val, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

def evaluate_tree(root):
    if not root:
        return 0
    
    # If the node is a leaf node, return its value (an integer)
    if not root.left and not root.right:
        return root.val
    
    # Otherwise, evaluate the left and right children
    left_val = evaluate_tree(root.left)
    right_val = evaluate_tree(root.right)
    
    # Apply the operation based on the node's value
    if root.val == '+':
        return left_val + right_val
    elif root.val == '-':
        return left_val - right_val
    elif root.val == '*':
        return left_val * right_val
    elif root.val == '/':
        return left_val / right_val
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