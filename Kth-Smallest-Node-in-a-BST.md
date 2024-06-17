*[[Unit 9 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 30+ mins
* 🛠️ **Topics**: Tree, Depth-First Search, Inorder Traversal
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Can k be greater than the number of nodes in the tree?
    - No, k will always be within the number of nodes in the tree as guaranteed by the problem statement.

- Can the tree have duplicate values?
    - No, all nodes in the tree are guaranteed to be unique.

```
HAPPY CASE

    3 (root)
   / \
  1   4
   \
    2

Input: root, k = 1
Output: 1
Explanation: The in-order traversal of the tree is [1,2,3,4]. The 1st smallest value is 1.
```
```
HAPPY CASE 2

      5 (root)
     / \
    3   6
   / \
  2   4
 /
1

Input: root, k = 3
Output: 3
Explanation: The in-order traversal of the tree is [1,2,3,4,5,6]. The 3rd smallest value is 3.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

For BST problems, we want to consider the following approaches:

- Inorder Traversal: Since an inorder traversal of a BST yields sorted node values, it is useful for finding the kth smallest node.
- Tree Traversal: Exploring the nodes in a specific order to get the desired result.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use an inorder traversal to get the nodes in sorted order, then return the k-th smallest node from the list.

```
1) Define a helper function `in_order_traversal(node)` to perform an inorder traversal.
    a) If the current node is None, return an empty list.
    b) Recursively perform inorder traversal on the left subtree and collect results.
    c) Add the current node's value to the list.
    d) Recursively perform inorder traversal on the right subtree and collect results.
    e) Return the concatenated list of left subtree, current node, and right subtree values.
2) In the main function `kth_smallest(root, k)`, call the helper function to get the sorted list of node values.
3) Return the k-th smallest value from the sorted list.
```

**⚠️ Common Mistakes**

- Forgetting to handle the case where the tree is empty.
- Not correctly performing the inorder traversal.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
class TreeNode:
    def __init__(self, val, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

def in_order_traversal(node):
    if not node:
        return []
    
    # Traverse the left subtree
    left = in_order_traversal(node.left)
    
    # Visit the current node
    current = [node.val]
    
    # Traverse the right subtree
    right = in_order_traversal(node.right)
    
    return left + current + right

def kth_smallest(root, k):
    # Perform in-order traversal to get the nodes in sorted order
    sorted_nodes = in_order_traversal(root)
    
    # Return the k-th smallest node
    return sorted_nodes[k - 1]
```
 
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with an input to check for the expected output
- Catch possible edge cases and off-by-one errors
- For a starting point, try checking your code against the Happy/Edge Case(s) above

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

Assume `N` represents the number of nodes in the tree.

* **Time Complexity**: `O(N)` because we need to traverse all the nodes in the tree.
* **Space Complexity**: `O(N)` for storing the node values during the inorder traversal.