*[[Unit 8 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 10 mins
* 🛠️ **Topics**: Trees, Binary Trees, Merging Trees
    
## 1: U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Question: What happens when one tree is significantly larger than the other?
    - Answer: Nodes from the larger tree will be used directly in parts of the merged tree where the smaller tree lacks corresponding nodes.

```
HAPPY CASE
Input: root1 = TreeNode(1, TreeNode(3, TreeNode(5), None), TreeNode(2)), root2 = TreeNode(2, TreeNode(1, None, TreeNode(4)), TreeNode(3, None, TreeNode(7)))
Output: TreeNode structure showing combined values.
Explanation: Nodes are merged by summing up values, resulting in a tree with nodes [3, 4, 5, 5, 4, 7].

EDGE CASE
Input: root1 = TreeNode(1), root2 = None
Output: TreeNode(1)
Explanation: Since root2 is None, the merged tree is the same as root1.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem is a variant of tree manipulation, specifically focusing on merging two binary trees. It tests understanding of tree traversal and node manipulation.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Traverse both trees simultaneously and sum their values at corresponding positions to form a new merged tree.

```
1) If both current nodes are null, return null.
2) If one node is null, return the other node.
3) Sum the values of both nodes and create a new tree node with this value.
4) Recursively merge the left children of both nodes and set it as the left child of the new node.
5) Recursively merge the right children of both nodes and set it as the right child of the new node.
6) Return the newly created node.
```

**⚠️ Common Mistakes**

- Not handling null nodes correctly, which could result in missing parts of the tree.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def merge_trees(root1, root2):
    """
    Merge two binary trees by rules defined.

    :param root1: The root of the first binary tree.
    :param root2: The root of the second binary tree.
    :return: The root of the merged binary tree.
    """
    if not root1 and not root2:
        return None
    elif not root1:
        return root2
    elif not root2:
        return root1
    
    # Merge the values if both nodes are present
    merged_root = TreeNode(root1.val + root2.val)
    
    # Recursively merge the left and right children
    merged_root.left = merge_trees(root1.left, root2.left)
    merged_root.right = merge_trees(root1.right, root2.right)
    
    return merged_root
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Test the function with various configurations of trees, especially focusing on cases with unbalanced sizes and null values.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(n)` where n is the number of nodes in the smaller tree. This is because each node in both trees needs to be visited at least once.
* **Space Complexity**: `O(m)` where m is the minimum height of the two trees. This is the space needed for the recursion stack, which can grow with the height of the smaller tree.
