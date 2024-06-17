*[[Unit 8 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 10 mins
* 🛠️ **Topics**: Trees, Binary Trees, Recursion
    
## 1: U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Question: What should the function return if the tree is empty?
    - Answer: The function should return 1 since the product of an empty set is defined as the multiplicative identity, which is 1.

```
HAPPY CASE
Input: TreeNode(2, TreeNode(3), TreeNode(5))
Output: 30
Explanation: The product of all node values (2 * 3 * 5) is 30.

EDGE CASE
Input: None
Output: 1
Explanation: The product of an empty tree is defined as 1.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem aligns with tree traversal problems that involve aggregating data from all nodes, such as calculating sums, products, or averages.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Recursively traverse the tree to calculate the product of values from all nodes.

```
1) If the current node is None, return 1 (as the neutral element of multiplication).
2) Recursively calculate the product of the left subtree.
3) Recursively calculate the product of the right subtree.
4) Multiply the current node's value by the products obtained from the left and right subtrees.
```

**⚠️ Common Mistakes**

- Returning 0 instead of 1 for None nodes, which would incorrectly turn the entire product to 0.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def product_tree(root):
    """
    Compute the product of all node values in the binary tree rooted at `root`.
    If the tree is empty, return 1 since it's a neutral element for multiplication.
    """
    if root is None:
        return 1
    return root.val * product_tree(root.left) * product_tree(root.right)
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Test with different tree configurations to ensure accuracy, especially with trees having zero or negative values.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(n)` where n is the number of nodes in the tree as each node is visited once.
* **Space Complexity**: `O(h)` where h is the height of the tree due to the recursion stack, potentially reaching `O(n)` in the case of a skewed tree.
