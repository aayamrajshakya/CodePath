*Originally from [[Unit 9 Session 1]] (Click for link to problem statements)*

*Reviewed in [[Unit 10 Session 2]]*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 30+ mins
* 🛠️ **Topics**: Tree, Recursion, Depth-First Search
* 📺 **Non-TIP101 Version**: [[Balanced Binary Tree]]

## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Can the tree be empty?
    - Yes, an empty tree is considered balanced.

- What should be returned for a single-node tree?
    - A single-node tree is balanced, so return True.

```
HAPPY CASE 1

    3 (root)
   / \
  9   20
     /  \
    15   7

Input: root
Output: True
Explanation: The tree is balanced as the height difference between the left and right subtrees of every node is not more than 1.
```
```
HAPPY CASE 2
 
        1 (root)
       / \
      2   2
     / \
    3   3
   / \
  4   4

Input: root
Output: False
Explanation: The tree is not balanced as the height difference between the left and right subtrees of the node with value 1 is more than 1.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

For Tree problems, we want to consider the following approaches:

- Depth-First Search (DFS): Useful for traversing the tree and calculating heights.
- Recursion: Effective for checking balance and height of subtrees.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use a recursive approach to check the balance of the tree. For each node, recursively check if the left and right subtrees are balanced and if the height difference is not more than 1.

```
1) Define a helper function `check_balance_and_height(node)` to check balance and calculate height.
    a) If the current node is None, return True (balanced) and height 0.
    b) Recursively check the left subtree for balance and height.
    c) Recursively check the right subtree for balance and height.
    d) Check if the current node is balanced by comparing the heights of the left and right subtrees.
    e) Calculate the height of the current node.
    f) Return if the current node is balanced and its height.
2) In the main function `is_balanced(root)`, call the helper function to start the check from the root node.
3) Return if the tree is balanced.
```

**⚠️ Common Mistakes**

- Forgetting to handle the case where the tree is empty.
- Not correctly calculating the height of the subtrees.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

def check_balance_and_height(node):
    if not node:
        return True, 0

    left_balanced, left_height = check_balance_and_height(node.left)
    right_balanced, right_height = check_balance_and_height(node.right)

    balanced = left_balanced and right_balanced and abs(left_height - right_height) <= 1
    height = max(left_height, right_height) + 1

    return balanced, height

def is_balanced(root):
    balanced, height = check_balance_and_height(root)
    return balanced
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