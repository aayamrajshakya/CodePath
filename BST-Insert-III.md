*[[Unit 8 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 10 mins
* 🛠️ **Topics**: Trees, Binary Search Trees, Insertion with Duplicates on the Left
    
## 1: U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Question: How should duplicates be handled in this particular insertion method?
    - Answer: If a node with the given value already exists, place the new node in the left subtree of the existing node.

```
HAPPY CASE
Input: TreeNode(20, TreeNode(10), TreeNode(30)), value = 25
Output: TreeNode structure with new TreeNode(25) under TreeNode(30).
Explanation: The value 25 is inserted correctly according to BST rules, fitting into the tree structure.

EDGE CASE
Input: TreeNode(20, TreeNode(10), TreeNode(30)), value = 20
Output: TreeNode structure with new TreeNode(20) inserted to the left of the existing TreeNode(20).
Explanation: As 20 is a duplicate, it's added to the left subtree of the existing 20 to maintain consistency.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This is a tree insertion problem with a twist on handling duplicates, often seen in systems that require maintaining historical data or versions in order.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Insert a new value into the binary search tree, with any duplicate values inserted to the left of the existing value.

```
1) If the tree is empty, insert the new node here.
2) If the new value is less than or equal to the current node's value, insert to the left.
3) If the new value is greater, insert to the right.
4) Return the unchanged root node, ensuring the tree remains connected.
```

**⚠️ Common Mistakes**

- Placing duplicates on the right or not handling them consistently, which could lead to incorrect tree behavior or structure.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def insert_with_duplicates(root, value):
    """
    Insert a new node with the given `value` into the binary search tree rooted at `root`,
    placing duplicates in the left subtree.
    """
    if root is None:
        return TreeNode(value)

    if value <= root.val:
        root.left = insert_with_duplicates(root.left, value)
    else:
        root.right = insert_with_duplicates(root.right, value)

    return root
```
    
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Test the function with equal values and different configurations to ensure duplicates are correctly placed to the left and the BST properties are maintained.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(h)` where h is the height of the tree, which could range from `O(log n)` in a balanced tree to `O(n)` in a skewed tree.
* **Space Complexity**: `O(h)` due to recursion, potentially reaching `O(n)` in a skewed scenario.
