*[[Unit 8 Session 1]] (Click for link to problem statements)*

*Looking for the recursive version of this problem?  Go to [[Find Leftmost Node I]]*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 10 mins
* 🛠️ **Topics**: Trees, Binary Trees, Iterative Algorithms
    
## 1: U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Question: What should be returned if the tree is empty?
    - Answer: The function should return None if the tree is empty.

```
HAPPY CASE
Input: TreeNode(1, TreeNode(2, TreeNode(4)), TreeNode(3))
Output: 4
Explanation: The leftmost node in the tree is the node with value 4, achieved by following the left children.

EDGE CASE
Input: TreeNode(1)
Output: 1
Explanation: The tree has only one node, which is also the leftmost node.
```
 
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem involves a straightforward tree traversal to locate the leftmost node, which aligns with iterative depth-first search methods.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Iteratively traverse to the leftmost node using a while loop until no left child is available.

```
1) Start at the root.
2) Use a loop to follow the left child until it no longer exists.
3) Return the value of the node where the loop terminates.
```

**⚠️ Common Mistakes**

- Not handling the case where the tree is empty, leading to attempts to access attributes of None.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def left_most(root):
    """
    Return the value of the leftmost node in the binary tree rooted at `root`.
    If the tree is empty, return None.
    """
    if root is None:
        return None
    # Traverse down to the leftmost child
    current = root
    while current.left is not None:
        current = current.left
    return current.val
```
   
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Verify with different test cases to ensure the function correctly identifies the leftmost node even in unbalanced trees.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(n)` in the worst case where n is the height of the tree, particularly if it is skewed to one side.
* **Space Complexity**: `O(1)` as no additional space is used apart from the input tree structure.
