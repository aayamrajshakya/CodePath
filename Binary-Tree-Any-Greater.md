*[[Unit 8 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 10 mins
* 🛠️ **Topics**: Trees, Binary Trees, Search Algorithms
    
## 1: U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Question: What if the tree is empty or the value does not exist in the tree?
    - Answer: Return False, as the value cannot be greater than any node in an empty tree or if it does not exist.

```
HAPPY CASE
Input: TreeNode(10, TreeNode(5), TreeNode(15, TreeNode(12), TreeNode(20))), value = 13
Output: True
Explanation: The value 20 is greater than 13 and exists in the tree.

EDGE CASE
Input: TreeNode(10, TreeNode(5), TreeNode(8)), value = 10
Output: False
Explanation: There is no node with a value greater than 10 in the tree.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem is a tree search challenge where the goal is to find if any node contains a value greater than a specified number. It resembles classic search operations but with a conditional twist to check values against a target.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Traverse the tree and check if any node has a value greater than the given value.

```
1) Start at the root.
2) If the current node is None, return False.
3) If the current node's value is greater than the given value, return True.
4) Recursively check both the left and right subtrees for a greater value.
```

**⚠️ Common Mistakes**

- Only checking the root or a subset of nodes, rather than ensuring all nodes are considered.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def contains_greater(node, value):
    """
    Checks if any node in the binary tree rooted at `node` contains a value greater than `value`.
    """
    if node is None:
        return False

    if node.val > value:
        return True

    # Recursively check the left and right subtrees
    return contains_greater(node.left, value) or contains_greater(node.right, value)
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Test the function with various configurations, including values that are not present and edge cases like empty trees.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(n)` where n is the number of nodes in the tree, as the worst case requires visiting every node.
* **Space Complexity**: `O(h)` where h is the height of the tree, due to recursion. This could be `O(n)` in a highly skewed tree.
