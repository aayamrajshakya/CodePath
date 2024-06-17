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
    - Answer: Return True, since technically an empty tree does not violate the condition of having all nodes with the same value.

```
HAPPY CASE
Input: TreeNode(5, TreeNode(5), TreeNode(5))
Output: True
Explanation: All nodes have the value 5, meeting the criteria of a uni-valued tree.

EDGE CASE
Input: None
Output: True
Explanation: An empty tree is considered uni-valued as there are no differing values.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem is a tree property validation challenge, often used in scenarios assessing data consistency across structured data.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Recursively verify that every node in the tree has the same value as the root node.

```
1) If the tree is empty, return True.
2) Start at the root and compare each node's value with the root’s value as you traverse the tree.
3) If all nodes match the root's value, return True; otherwise, return False.
```

**⚠️ Common Mistakes**

- Incorrectly handling trees with only one node or returning False for an empty tree.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```markdown
def is_univalued_helper(node, value):
    """
    Helper function to determine if the current node and all its descendants have the same value.
    """
    if not node:
        return True

    if node.val != value:
        return False

    return is_univalued_helper(node.left, value) and is_univalued_helper(node.right, value)

def is_univalued(root):
    """
    Check if a binary tree is uni-valued, i.e., all nodes contain the same value.
    """
    if not root:
        return True

    return is_univalued_helper(root, root.val)
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Test with varied tree structures to confirm the function accurately checks for uniformity in node values.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(n)` where n is the number of nodes in the tree, as each node is checked for value uniformity.
* **Space Complexity**: `O(h)` where h is the height of the tree due to recursion depth, potentially reaching `O(n)` in a skewed tree.
