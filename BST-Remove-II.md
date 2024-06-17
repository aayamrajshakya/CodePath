*[[Unit 8 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 20 mins
* 🛠️ **Topics**: Trees, Binary Search Trees, Node Deletion, In-Order Predecessor
    
## 1: U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Question: How should the function handle deletion when a node has two children?
    - Answer: Use the in-order predecessor, which is the largest node in its left subtree, to replace the node.

```
HAPPY CASE
Input: TreeNode(20, TreeNode(10, TreeNode(5), TreeNode(15)), TreeNode(30)), key = 10
Output: TreeNode structure with TreeNode(5) replacing the deleted node (10).
Explanation: Node 10 is replaced by its in-order predecessor, 5.

EDGE CASE
Input: TreeNode(20), key = 20
Output: None
Explanation: The root node is deleted and there are no other nodes to replace it.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem is a classic node deletion scenario in a binary search tree, which is essential for operations that require removing specific elements while maintaining the sorted structure of the tree.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Navigate to the node, adjust the tree structure based on the node's children, and if it has two children, use the in-order predecessor.

```
1) If the node to be deleted has no children, simply remove it.
2) If the node has one child, replace the node with its child.
3) If the node has two children, find the in-order predecessor (largest in the left subtree), swap it with the node, and then correctly remove the predecessor node.
4) Ensure the BST properties are maintained throughout the process.
```

**⚠️ Common Mistakes**

- Not correctly reconnecting the children of the in-order predecessor.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def remove_bst(root, key):
    """
    Remove a node with a given key from the BST using the in-order predecessor method and return the new root.
    """
    if not root:
        return None

    # Locate the node to remove
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

        # Node with two children: use the in-order predecessor
        temp_val = find_rightmost(root.left)
        root.val = temp_val
        root.left = remove_bst(root.left, temp_val)

    return root

def find_rightmost(node):
    """
    Find the rightmost (largest) node starting from the given node.
    """
    current = node
    while current.right:
        current = current.right
    return current.val
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Ensure that the tree maintains its BST properties after deletion and that all pointers are correctly updated.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(h)` where h is the height of the tree. In the worst case for a skewed tree, this could be `O(n)`.
* **Space Complexity**: `O(h)` due to recursion, which can become `O(n)` in the worst-case scenario.
