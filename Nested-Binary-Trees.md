*[[Unit 8 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 15 mins
* 🛠️ **Topics**: Trees, Binary Trees, Subtree Checking
    
## 1: U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Question: How should the function handle cases where either the main tree or the subtree is empty?
    - Answer: If the main tree is empty and the subtree is not, return False. If the subtree is empty, return True, as an empty subtree is always a subtree of any tree.

```
HAPPY CASE
Input: root = TreeNode(3, TreeNode(4, TreeNode(1), TreeNode(2)), TreeNode(5)), sub_root = TreeNode(4, TreeNode(1), TreeNode(2))
Output: True
Explanation: The subtree starting with node 4 matches the structure and values of sub_root.

EDGE CASE
Input: root = TreeNode(1), sub_root = None
Output: True
Explanation: An empty subtree is a subtree of any tree, including a single-node tree.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g., Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem is essentially a tree traversal and matching problem, involving checking each node for a match with the subtree's root and verifying subsequent structure and values.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Traverse the main tree to find a node that matches the root of the subtree and then verify that the entire subtree structure matches from that point.

```
1) If either the main tree or the subtree root is null, handle base cases.
2) For each node in the main tree that matches the subtree's root, check if the subtree starting from this node matches the given subtree.
3) Use a helper function to compare two trees for equality.
```

**⚠️ Common Mistakes**

- Failing to check every node in the main tree that matches the subtree's root, leading to missed potential matches.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def is_subtree(root, sub_root):
    """
    Determine if `sub_root` is a subtree of `root`.
    """
    if not sub_root:
        return True  # An empty subtree is a subtree of any tree
    if not root:
        return False  # Non-empty subtree cannot be a subtree of an empty tree

    if is_same_tree(root, sub_root):
        return True
    return is_subtree(root.left, sub_root) or is_subtree(root.right, sub_root)

def is_same_tree(s, t):
    """
    Helper function to determine if two trees are identical.
    """
    if not s and not t:
        return True
    if not s or not t:
        return False
    return s.val == t.val and is_same_tree(s.left, t.left) and is_same_tree(s.right, t.right)
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Test with different tree and subtree combinations, including cases where the subtree appears more than once in the tree.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(n * m)` where n is the number of nodes in the main tree and m is the number of nodes in the subtree. This reflects the worst-case scenario where each node in the main tree needs to be compared to the subtree.
* **Space Complexity**: `O(h)` where h is the height of the main tree, which influences the recursion stack depth.
