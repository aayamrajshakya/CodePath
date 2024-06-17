*[[Unit 10 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 20 mins
* 🛠️ **Topics**: Tree, Depth-First Search (DFS)
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- What should be returned if one of the trees is empty?
    - False, unless both trees are empty, in which case they are trivially similar.

```
HAPPY CASE
Input: root1 = [3, 5, 1, 6, 2, 9, 8, null, null, 7, 4], root2 = [3, 5, 1, 6, 7, 4, 2, null, null, null, null, null, null, 9, 8]
Output: True
Explanation: Both trees have the leaf value sequence [6, 7, 4, 9, 8].

HAPPY CASE
Input: root1 = [1, 2, 3], root2 = [1, 3, 2]
Output: False
Explanation: The leaf value sequences are [2, 3] and [3, 2], which are different.

EDGE CASE
Input: root1 = [], root2 = []
Output: True
Explanation: Both trees are empty, so they are trivially similar.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

For Tree problems, we want to consider the following approaches:

- Using Depth-First Search (DFS) to traverse the tree and collect the leaf nodes in a list.
- Comparing the lists of leaf nodes from both trees.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use DFS to collect the leaf nodes of each tree in a list. Compare the two lists to determine if the trees are leaf-similar.

```
1) Define a helper function `get_leaves(node)` that:
    a) Returns an empty list if the node is None.
    b) Returns a list with the node's value if it is a leaf node (both left and right children are None).
    c) Recursively collects leaves from the left and right subtrees and combines them.
2) Use the helper function to collect leaves from both `root1` and `root2`.
3) Compare the two lists of leaves.
4) Return True if the lists are equal, otherwise return False.
```

**⚠️ Common Mistakes**

- Not correctly handling the case where one or both trees are empty.
- Incorrectly collecting or combining the leaf nodes.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```
def leaf_similar(root1, root2):
    def get_leaves(node):
        if not node:
            return []
        if not node.left and not node.right:
            return [node.val]
        return get_leaves(node.left) + get_leaves(node.right)
    
    return get_leaves(root1) == get_leaves(root2)
```
 
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with an input to check for the expected output.
- Example: Trace with root1 = [3, 5, 1, 6, 2, 9, 8, null, null, 7, 4], root2 = [3, 5, 1, 6, 7, 4, 2, null, null, null, null, null, null, 9, 8]
    - get_leaves(root1) = [6, 7, 4, 9, 8]
    - get_leaves(root2) = [6, 7, 4, 9, 8]
    - Compare the two lists and return True

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

Assume `N` and `M` represent the number of nodes in `root1` and `root2` respectively.

* **Time Complexity**: `O(N + M)` because we need to traverse all nodes in both trees.
* **Space Complexity**: `O(N + M)` because we need to store the leaf nodes of both trees in lists.