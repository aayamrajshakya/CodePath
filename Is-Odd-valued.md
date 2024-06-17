*[[Unit 8 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 10 mins
* 🛠️ **Topics**: Trees, Binary Trees, Value Counting
    
## 1: U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Question: How should the function handle an empty tree?
    - Answer: Return 0, as there are no nodes to count.

```
HAPPY CASE
Input: TreeNode(3, TreeNode(1), TreeNode(5))
Output: 2
Explanation: The nodes with values 3 and 5 have odd values.

EDGE CASE
Input: None
Output: 0
Explanation: An empty tree has no nodes, so the count is 0.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g., Linked List or Dynamic Programming, and strategies or patterns in those categories.

This is a tree traversal problem where the task is to count nodes based on a specific property (odd values in this case). It's similar to problems involving data summarization or aggregation.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use a recursive approach to traverse the tree and count nodes with odd values.

```
1) If the current node is None, return 0.
2) Check if the current node's value is odd.
3) Recursively count odd nodes in both the left and right subtree.
4) Return the total count of odd nodes.
```

**⚠️ Common Mistakes**

- Incorrectly handling or counting node values, or misunderstanding the odd value condition.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def count_odds(node):
    """
    Recursive function to count the number of nodes with odd values.
    """
    if not node:
        return 0

    # Check if the current node's value is odd
    is_odd = 1 if node.val % 2 != 0 else 0

    # Recursively count odd nodes in both subtrees
    return is_odd + count_odds(node.left) + count_odds(node.right)
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Test the function with various tree sizes and structures to ensure accurate counts are obtained across all configurations.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(n)` where n is the number of nodes in the tree, as each node must be visited and checked.
* **Space Complexity**: `O(h)` where h is the height of the tree due to the recursion stack, potentially reaching `O(n)` in a highly skewed tree.
