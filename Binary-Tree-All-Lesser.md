*[[Unit 8 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 10 mins
* 🛠️ **Topics**: Trees, Binary Trees, Recursive Algorithms
    
## 1: U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Question: What should the function return for an empty tree?
    - Answer: Return False because a tree with no nodes cannot have nodes less than a given value.

```
HAPPY CASE
Input: TreeNode(3, TreeNode(2), TreeNode(4)), val = 5
Output: True
Explanation: All nodes in the tree have values less than 5.

EDGE CASE
Input: TreeNode(6, TreeNode(5), TreeNode(7)), val = 5
Output: False
Explanation: The root node and its right child have values greater than or equal to 5.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem is a typical recursive traversal problem, where the task is to verify a property (node value comparison) across all nodes in a binary tree.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use recursion to traverse the tree and check if all node values are less than the given value.

```
1) Start at the root. If the root is None, return False (an empty tree cannot satisfy the condition).
2) If the root's value is greater than or equal to the given value, return False.
3) Recursively check the left subtree and the right subtree.
4) Return True if both subtrees satisfy the condition.
```

**⚠️ Common Mistakes**

- Incorrect base case handling, such as returning True for an empty tree which should return False as per the problem's specific requirements.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def is_lesser(root, val):
    """
    Return True if all nodes in the binary tree rooted at `root` have values less than `val`.
    If the tree is empty, return False.
    """
    if root is None:
        return False  # An empty tree should return False according to the specification

    # Check the value of the current node
    if root.val >= val:
        return False

    # Recursively check the left and right subtrees
    left_check = is_lesser(root.left, val)
    right_check = is_lesser(root.right, val)

    return left_check and right_check
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Validate with various tree configurations and different values to ensure that all nodes are correctly evaluated against the specified value.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(n)` where n is the number of nodes in the tree as each node is visited once.
* **Space Complexity**: `O(h)` where h is the height of the tree, due to the recursion stack, potentially reaching `O(n)` in the case of a skewed tree.
