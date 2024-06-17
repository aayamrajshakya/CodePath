*[[Unit 8 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 20 mins
* 🛠️ **Topics**: Trees, Binary Search Trees, Node Deletion
    
## 1: U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Question: What strategy should be used to handle deletion when a node has two children?
    - Answer: Use the in-order successor of that node, which is the smallest value in its right subtree, to replace the node.

```
HAPPY CASE
Input: TreeNode(10, TreeNode(5), TreeNode(15, TreeNode(12), TreeNode(20))), key = 15
Output: TreeNode structure with TreeNode(12) replacing the deleted node (15).
Explanation: Node 15 is replaced by its in-order successor, 20.

EDGE CASE
Input: TreeNode(10, TreeNode(5), TreeNode(15)), key = 10
Output: TreeNode structure with TreeNode(15) as the new root.
Explanation: Root node is deleted and replaced by its in-order successor, 15.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem is a classic node deletion scenario in a binary search tree, which is fundamental for maintaining the integrity of data structures while allowing dynamic data modification.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Navigate the tree to locate the node to be deleted, then adjust the tree structure based on the node's number of children.

```
1) If the node to be deleted has no children, simply remove it.
2) If the node has one child, replace the node with its child.
3) If the node has two children, replace the node with its in-order successor and remove the successor from its original position.
4) Maintain the BST properties throughout the process.
```

**⚠️ Common Mistakes**

- Failing to correctly reconnect the children of the in-order successor.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def remove_bst(root, key):
    """
    Remove a node with a given key from the BST and return the new root.
    """
    if not root:
        return None

    # Find the node to delete
    if key < root.val:
        root.left = remove_bst(root.left, key)
    elif key > root.val:
        root.right = remove_bst(root.right, key)
    else:
        # Node with only one child or no child
        if not root.left:
            return root.right
        elif not root.right:
            return root.left

        # Node with two children, get the in-order successor (smallest in the right subtree)
        temp_val = find_min(root.right)
        root.val = temp_val
        root.right = remove_bst(root.right, temp_val)

    return root

def find_min(node):
    """
    Find the smallest value in the BST.
    """
    current = node
    while current.left is not None:
        current = current.left
    return current.val
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Ensure that the tree maintains its BST properties after deletion and that all pointers are correctly updated.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(h)` where h is the height of the tree. In the worst case for a skewed tree, this could be `O(n)`.
* **Space Complexity**: `O(h)` due to recursion, which can become `O(n)` in the worst-case scenario.
