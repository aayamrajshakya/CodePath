*[[Unit 8 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 10 mins
* 🛠️ **Topics**: Trees, Binary Search Trees, Search Algorithms
    
## 1: U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Question: What happens if the value is exactly equal to a node's value that isn't a leaf?
    - Answer: If the node is not a leaf, it should still return False because the function specifically checks for leaf nodes.

```
HAPPY CASE
Input: TreeNode(10, TreeNode(5, TreeNode(3), TreeNode(8)), TreeNode(15, TreeNode(12), TreeNode(20))), value = 20
Output: True
Explanation: The node with value 20 is a leaf and it exists in the tree, thus fulfilling the condition.

EDGE CASE
Input: TreeNode(10), value = 10
Output: False
Explanation: The node with value 10 is not a leaf because it's also the root with no children.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem is a targeted search problem within a binary search tree (BST), making use of BST properties to efficiently determine if a given value not only exists in the tree but also checks if it's a leaf.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use binary search tree properties to navigate to the node and verify if it is a leaf.

```
1) Start at the root.
2) Use the BST property to navigate: 
  a) if the value is less than the current node's, go left
  b) if more, go right.
3) If you find the node and it has no children, return True.
4) If the node isn't found or isn't a leaf, return False.
```

**⚠️ Common Mistakes**

- Misunderstanding the definition of a leaf (a node with no children).
- Not leveraging BST properties, which can lead to inefficient search.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def contains_greater_bst(node, value):
    """
    Returns `True` if any node in the binary search tree rooted at `node` has a value greater than `value`.
    Otherwise, returns `False`.
    """
    if node is None:
        return False

    # If the current node's value is greater than `value`, it's a candidate,
    # and we also need to search the left subtree for other candidates.
    if node.val > value:
        return True

    # Since we're searching for a value greater than `value`, explore the right subtree only
    return contains_greater_bst(node.right, value)
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Verify through several examples where values are both present and not present, and both as leaves and non-leaves, to ensure complete accuracy.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(log n)` on average, where n is the number of nodes in the tree. This assumes the tree is balanced, thus the height is about log(n).
* **Space Complexity**: `O(log n)` due to the recursion depth, also assuming a balanced tree.
