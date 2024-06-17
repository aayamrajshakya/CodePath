*[[Unit 8 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 5 mins
* 🛠️ **Topics**: Trees, Binary Trees, Conditional Statements
    
## 1: U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Question: How does the function handle trees with fewer than three nodes?
    - Answer: The function returns False if any child node is missing.

```
HAPPY CASE
Input: TreeNode(5, TreeNode(2), TreeNode(3))
Output: True
Explanation: 2 + 3 = 5, which equals the root's value.

EDGE CASE
Input: TreeNode(5, TreeNode(2), None)
Output: False
Explanation: The tree is missing one child node, so the comparison cannot be made properly.
```
 
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem is a variation of the tree validation problem, where we check a specific condition related to the node values in a very small tree.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Ensure that the tree structure is complete and check if the sum of the children's values equals the root's value.

```
1) Check if the root or any children are None.
2) If all nodes are present, compute the sum of the children's values.
3) Compare the sum with the root's value.
4) Return True if they are equal, otherwise return False.
```

**⚠️ Common Mistakes**

- Ignoring cases where the tree does not have exactly three nodes, which can lead to incorrect comparisons or errors.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def check_tree(root):
    if not root:
        return False
    left_val = right_val = 0
    if root.left:
        left_val = root.left.val
    if root.right:
        right_val = root.right.val           
    child_sum = left_val + right_val          
    return root.val == child_sum
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Test with both the happy case and various edge cases (missing children, tree is None) to confirm the function handles all scenarios.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(1)` as the function performs a constant amount of work regardless of input size.
* **Space Complexity**: `O(1)` because it uses a fixed amount of space.
