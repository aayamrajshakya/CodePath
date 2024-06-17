*[[Unit 8 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 15 mins
* 🛠️ **Topics**: Trees, Binary Search Trees, Insertion, Handling Duplicates
    
## 1: U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Question: How does the tree handle duplicate values?
    - Answer: If a duplicate value is inserted, it should be placed in the right subtree to maintain a consistent approach.

```
HAPPY CASE
Input: TreeNode(20, TreeNode(10), TreeNode(30)), value = 25
Output: TreeNode structure with new TreeNode(25) under TreeNode(30).
Explanation: The value 25 fits between the values 20 and 30, and is added to the right subtree of 20.

EDGE CASE
Input: TreeNode(20, TreeNode(10), TreeNode(30)), value = 20
Output: TreeNode structure with new TreeNode(20) under TreeNode(30).
Explanation: As 20 is a duplicate, it's added to the right subtree of the existing 20.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem is a typical binary search tree insertion, which is fundamental for operations in a sorted data structure. Handling duplicates by placing them consistently in the left subtree ensures order and retrievability.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Insert the new value into the tree following BST rules and handling duplicates by inserting them into the right subtree.

```
1) If the tree is empty, insert the new node here.
2) If the new value is less, recurse into the left subtree.
3) If the new value is greater or equal (to handle duplicates), recurse into the right subtree.
4) Return the unchanged root node.
```

**⚠️ Common Mistakes**

- Placing duplicates in the left subtree or not allowing duplicates at all, which could lead to unexpected behavior or data loss.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
"def insert_with_duplicates(root, value):
    """"""
    Insert a new node with the given `value` into the binary search tree rooted at `root`.
    Allows duplicates to be inserted into the right subtree.
    """"""
    if root is None:
        return TreeNode(value)

    if value < root.val:
        root.left = insert_with_duplicates(root.left, value)
    else:
        # Duplicates and greater values go to the right subtree
        root.right = insert_with_duplicates(root.right, value)

    return root"
```
    
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Test the function with values equal to existing node values to ensure duplicates are correctly handled, and ensure the tree maintains its BST properties.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(h)` where h is the height of the tree, potentially `O(log n)` in a balanced BST but could degrade to `O(n)` if the tree becomes skewed.
* **Space Complexity**: `O(h)` for the recursion depth, which may also degrade depending on the tree’s balance.
