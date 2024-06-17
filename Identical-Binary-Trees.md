*[[Unit 8 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 15 mins
* 🛠️ **Topics**: Trees, Binary Trees, Comparison, Identical Trees
    
## 1: U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Question: What constitutes identical trees?
    - Answer: Two trees are considered identical if they are structurally identical and all corresponding nodes contain the same value.

```
HAPPY CASE
Input: root1 = TreeNode(1, TreeNode(2), TreeNode(3)), root2 = TreeNode(1, TreeNode(2), TreeNode(3))
Output: True
Explanation: Both trees are structurally the same and have the same values at corresponding positions.

EDGE CASE
Input: root1 = TreeNode(1), root2 = TreeNode(1, TreeNode(2), None)
Output: False
Explanation: The trees have different structures, hence they are not identical.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g., Linked List or Dynamic Programming, and strategies or patterns in those categories.

This is a tree comparison problem that tests for complete equality in structure and value between two binary trees.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Recursively compare each node of the two trees to check for both structural and value equality.

```
1) If both trees are empty, they are identical.
2) If one tree is empty and the other is not, they are not identical.
3) Compare the current node of both trees for equality in value.
4) Recursively compare the left subtree of both trees.
5) Recursively compare the right subtree of both trees.
6) Return true only if all comparisons are true.
```

**⚠️ Common Mistakes**

- Failing to check both structure and value, or incorrectly handling one or both trees being empty.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def is_identical(root1, root2):
    """
    Determine whether two binary trees are identical.
    """
    if not root1 and not root2:
        return True
    if not root1 or not root2:
        return False

    # Check current nodes and recursively check left and right subtrees
    return (
        root1.val == root2.val and
        is_identical(root1.left, root2.left) and
        is_identical(root1.right, root2.right)
    )
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Test with various tree structures to ensure accuracy in identification of identical trees.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(n)` where n is the number of nodes in the smaller tree, as it requires comparing each node in both trees.
* **Space Complexity**: `O(h)` where h is the height of the smaller tree due to the recursion stack depth.
