*[[Unit 8 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 20 mins
* 🛠️ **Topics**: Trees, Binary Search Trees, Node Deletion by Merging
    
## 1: U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Question: What is deletion by merging?
    - Answer: When deleting a node with two children, attach the root of the right subtree directly to the largest node of the left subtree. This method keeps the remaining subtree structure intact.

```
HAPPY CASE
Input: TreeNode(20, TreeNode(10, TreeNode(5), TreeNode(15)), TreeNode(30)), key = 20
Output: TreeNode structure with TreeNode(15) merging the right subtree.
Explanation: Node 20 is deleted, and TreeNode 15 becomes the new root, with TreeNode 30 attached to it.

EDGE CASE
Input: TreeNode(10), key = 10
Output: None
Explanation: Deleting the only node results in an empty tree.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g., Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem deals with the structured manipulation of a binary search tree during deletion, which requires understanding of tree dynamics and maintaining the BST properties.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Delete a node by merging subtrees, specifically by attaching the right subtree to the largest node of the left subtree when deleting a node with two children.

```
1) Identify the node to be deleted.
2) If the node has no children, simply remove it.
3) If the node has one child, replace it with that child.
4) If the node has two children, find the largest node in the left subtree (in-order predecessor), and merge the right subtree with this node.
5) Adjust pointers to maintain the BST properties.
```

**⚠️ Common Mistakes**

- Failing to correctly merge the subtrees, which could disrupt the BST structure.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def remove_bst(root, key):
    """
    Remove a node from a BST using deletion by merging strategy.
    """
    if not root:
        return None

    # Locate the node to remove
    if key < root.val:
        root.left = remove_bst(root.left, key)
    elif key > root.val:
        root.right = remove_bst(root.right, key)
    else:
        # Node found; handle different removal cases
        if not root.left and not root.right:
            # Leaf node
            return None
        elif not root.left:
            # Only right child
            return root.right
        elif not root.right:
            # Only left child
            return root.left
        else:
            # Node with two children: perform deletion by merging
            largest_left = find_largest(root.left)
            largest_left.right = root.right
            return root.left

    return root

def find_largest(node):
    """
    Find the largest node starting from the given node.
    """
    current = node
    while current.right:
        current = current.right
    return current
```
   
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Ensure that the tree maintains its BST properties after deletion and that all pointers are correctly updated.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(h)` where h is the height of the tree. In the worst case for a skewed tree, this could be `O(n)`.
* **Space Complexity**: `O(h)` due to recursion, which can become `O(n)` in the worst-case scenario.
