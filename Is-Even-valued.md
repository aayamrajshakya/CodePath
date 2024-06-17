*[[Unit 8 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 10 mins
* 🛠️ **Topics**: Trees, Binary Trees, Property Checking
    
## 1: U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Question: How should the function handle an empty tree?
    - Answer: Return True, as an empty tree trivially satisfies the condition of all nodes having even values.

```
HAPPY CASE
Input: TreeNode(4, TreeNode(6), TreeNode(8))
Output: True
Explanation: All node values (4, 6, 8) are even.

EDGE CASE
Input: TreeNode(4, TreeNode(7), TreeNode(8))
Output: False
Explanation: Not all node values are even; the node with value 7 is odd.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This is a tree traversal problem where the task is to check a property (evenness of node values) across all nodes in a binary tree.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Traverse the tree using a recursive approach to check if all node values are even.

```
1) If the tree is empty, return True.
2) Check if the value of the current node is even.
3) Recursively verify that both the left and right subtree nodes are also even.
4) Return False immediately if any node is found with an odd value.
```

**⚠️ Common Mistakes**

- Incorrectly handling the base case or failing to terminate early upon finding an odd value.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def is_even_helper(node):
    """
    Helper function to determine if the current node and all its descendants have even values.
    """
    if not node:
        return True

    # Check if the current node's value is even
    if node.val % 2 != 0:
        return False

    # Recursively check both subtrees
    return is_even_helper(node.left) and is_even_helper(node.right)

def is_even(root):
    """
    Check if all nodes in the binary tree contain even values.
    """
    return is_even_helper(root)
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Test with a variety of trees to ensure the function correctly identifies trees with only even values and rejects those with any odd values.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(n)` where n is the number of nodes in the tree, as each node must be checked.
* **Space Complexity**: `O(h)` where h is the height of the tree due to recursion, which could be `O(n)` in a skewed tree.
