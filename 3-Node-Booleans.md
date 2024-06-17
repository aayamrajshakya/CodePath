*[[Unit 8 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 5 mins
* 🛠️ **Topics**: Trees, Binary Trees, Boolean Logic
    
## 1: U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

```
HAPPY CASE
Input: TreeNode('AND', TreeNode(True), TreeNode(False))
Output: False
Explanation: The 'AND' operation between True and False yields False.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem involves evaluating a simple Boolean expression represented in a binary tree format, where the root node defines the operation (AND/OR) and the children provide the operands.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use the value of the root node to determine which Boolean operation to perform on the values of its children.

```
1) Retrieve the Boolean values from the children nodes.
2) Perform the operation specified by the root's value on the children's values.
3) Return the result of the operation.
```

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def tree_expression(root):
    """
    Evaluates a boolean operation ('AND' or 'OR') stored in the root node on its two child nodes.
    """

    # Retrieve the boolean values from the children
    left_value = root.left.val
    right_value = root.right.val
    
    # Perform the operation based on the root's value
    if root.val == 'AND':
        return left_value and right_value
    elif root.val == 'OR':
        return left_value or right_value
    else:
        return False
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Test the function with all combinations of True and False for both 'AND' and 'OR' operations to ensure accuracy.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(1)` as the function only checks and processes three nodes regardless of any other factors.
* **Space Complexity**: `O(1)` because no extra space is used beyond the input nodes.
