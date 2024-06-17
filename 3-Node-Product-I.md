*[[Unit 8 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 5 mins
* 🛠️ **Topics**: Trees, Binary Trees, Math Operations
    
## 1: U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

```
HAPPY CASE
Input: TreeNode(6, TreeNode(2), TreeNode(3))
Output: True
Explanation: The product of the values of the two children (2 * 3) equals the value of the root (6).
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem is a typical validation problem within the tree structure that checks if a node’s value corresponds to a specific relation with its children's values (in this case, a product relation).

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Check if the root's value equals the product of its children’s values.

```
1) Calculate the product of the children's values.
2) Compare the product with the root's value.
3) Return True if they match, else return False.
```

**⚠️ Common Mistakes**

- Incorrect handling of cases where the tree has missing children, which would lead to incorrect calculations or exceptions.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def check_tree(root):
	return root.val == root.left.val * root.right.val
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Test with various configurations of the tree to ensure correctness, especially where children nodes might be missing.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(1)` as the operation only involves a direct comparison after a single multiplication.
* **Space Complexity**: `O(1)` because no additional space is used beyond the existing tree nodes.
