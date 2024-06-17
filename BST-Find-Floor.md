*[[Unit 8 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 20 mins
* 🛠️ **Topics**: Binary Search Trees, Tree Traversal
    
## 1: U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Is the tree guaranteed to have unique values?
    - Assume all values in the tree are unique.

HAPPY CASE
Input: root = TreeNode(10), value = 7
Output: 5
Explanation: The largest value less than or equal to 7 in the tree rooted at 10 is 5.

EDGE CASE
Input: root = TreeNode(10), value = 0
Output: None
Explanation: There are no values less than or equal to 0 in the tree.

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

For Binary Search Tree problems, we want to consider the following approaches:

- Traverse the tree while maintaining a reference to the candidate node that fits the criteria.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Traverse the tree from the root and keep track of the node that best fits the condition as you traverse.

1) Start from the root node.
2) If the current node's value is greater than the given value, move to the left child.
3) If the current node's value is less than or equal to the given value, update the floor value and move to the right child.
4) If the end of the path is reached, return the last recorded floor value, or None if no valid floor was found.

**⚠️ Common Mistakes**

- Not updating the floor value correctly when a valid candidate is found.
- Failing to handle the case where no valid floor exists.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def find_floor(root, value):
    """
    Find the largest value in the BST less than or equal to the given value.
    """
    floor_value = None
    
    while root:
        if root.val == value:
            # If we find the exact value, it's the floor
            return root.val
        elif root.val < value:
            # Potential floor, move to the right subtree
            floor_value = root.val
            root = root.right
        else:
            # Move to the left subtree
            root = root.left
    
    return floor_value
```


## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with an input to check for the expected output
- Catch possible edge cases and off-by-one errors

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(log n)` for a balanced binary search tree, because each step halves the number of nodes to examine.
* **Space Complexity**: `O(1)` because we only use a few pointers for iteration.
