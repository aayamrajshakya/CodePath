*[[Unit 8 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy to Medium
* ⏰ **Time to complete**: 15 mins
* 🛠️ **Topics**: Trees, Binary Search Trees, Successor Finding
    
## 1: U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Question: How should the function handle cases where there is no in-order successor in the tree?
    - Answer: Return None if there is no in-order successor (e.g., when the given node is the rightmost node).

```
HAPPY CASE
Input: BST with nodes [20, 9, 25, 5, 12], find in-order successor of 12
Output: 20
Explanation: 20 is the next node in in-order traversal after 12.

EDGE CASE
Input: BST with nodes [20, 9, 25, 5, 12], find in-order successor of 25
Output: None
Explanation: 25 is the rightmost node, and there is no successor.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem is primarily a tree navigation problem, specifically dealing with the properties of binary search trees to find the in-order successor.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Utilize the BST properties to efficiently find the in-order successor.

```
1) If the node has a right subtree, the successor is the leftmost node in that subtree.
2) If the node has no right subtree, the successor is one of its ancestors; specifically, the nearest ancestor for which the given node is in its left subtree.
```

**⚠️ Common Mistakes**

- Failing to check both cases: node has a right subtree or no right subtree, leading to incorrect or incomplete results.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def inorder_successor(root, node):
    """
    Find the in-order successor of a given node in a binary search tree.
    """
    if node.right:
        # The successor is the leftmost node of the right subtree
        return find_min(node.right)

    # Traverse up the ancestors
    successor = None
    while root:
        if node.val < root.val:
            successor = root
            root = root.left
        elif node.val > root.val:
            root = root.right
        else:
            break
    return successor

def find_min(node):
    """
    Find the smallest node in a subtree.
    """
    while node.left:
        node = node.left
    return node
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Test with a variety of tree configurations and node positions to ensure that the successor is correctly identified.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(h)` where h is the height of the tree. This operation requires traversal up to the root or down to a leaf.
* **Space Complexity**: `O(1)` as it only requires a few pointers without additional data structures.
