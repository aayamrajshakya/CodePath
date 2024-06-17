*[[Unit 8 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 20 mins
* 🛠️ **Topics**: Trees, Binary Search Trees, In-Order Predecessor

## 1: U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Question: What should be done if there is no in-order predecessor available?
    - Answer: Return None if there is no in-order predecessor, such as when the node is the leftmost node.

```
HAPPY CASE
Input: BST with nodes [20, 10, 30, 5, 15], search in-order predecessor of 10
Output: 5
Explanation: 5 is the in-order predecessor of 10 as it is the largest value less than 10.

EDGE CASE
Input: BST with nodes [20, 10, 30, 5, 15], search in-order predecessor of 5
Output: None
Explanation: 5 is the leftmost node, so it has no predecessor.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g., Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem involves navigating through a binary search tree (BST) to find the in-order predecessor, utilizing the properties of BSTs to efficiently find the required node.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Utilize the properties of BSTs to find the in-order predecessor of a node.

```
1) If the node has a left subtree, the in-order predecessor is the rightmost node of this subtree.
2) If the node has no left subtree, the predecessor is one of its ancestors; specifically, the nearest ancestor for which this node is in the right subtree.
3) Traverse the tree from the root to find the node and keep track of the potential predecessor.
```

**⚠️ Common Mistakes**

- Incorrectly identifying the in-order predecessor or failing to handle the absence of a left subtree.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def inorder_predecessor(root, current):
    """
    Find the in-order predecessor of a given node in a BST.
    """
    predecessor = None
    while root:
        if current.val > root.val:
            predecessor = root
            root = root.right
        elif current.val < root.val:
            root = root.left
        else:
            if root.left:
                predecessor = find_rightmost(root.left)
            break
    return predecessor

def find_rightmost(node):
    """
    Find the rightmost (largest) node starting from the given node.
    """
    while node.right:
        node = node.right
    return node
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Ensure correct in-order predecessor identification in various configurations, especially where nodes do not have a left subtree.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(h)` where h is the height of the tree. This ensures efficient traversal up to the root or down to a leaf, depending on the node's position.
* **Space Complexity**: `O(1)` as it only requires maintaining a few pointers without additional structures.
