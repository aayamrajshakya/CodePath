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

- Can the tree have duplicate values?
    - No, it is a binary search tree (BST) which has unique values.

- What should be returned if the tree has only one node?
    - This situation won't occur since the problem specifies different nodes.

```
HAPPY CASE

      4 (root)
     / \
    2   6
   / \
  1   3

Input: root
Output: 1
Explanation: The minimum difference is between nodes 2 and 3, or nodes 1 and 2.
```
```
EDGE CASE

    1 (root)

Input: root
Output: inf
Explanation: There is only one node, hence no valid answer.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

For BST problems, we want to consider the following approaches:

- Inorder Traversal: Since an inorder traversal of a BST yields sorted node values, it is useful for finding minimum differences.
- Tree Traversal: Exploring different tree traversal methods to compare node values.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Perform an inorder traversal of the BST to get a sorted list of node values. Then, find the minimum difference between consecutive values in this list.

```
1) Initialize an empty list to store node values.
2) Define a helper function `inorder_traversal(root, nodes)` to perform an inorder traversal.
    a) If the current node is None, return.
    b) Recursively call the helper function for the left child.
    c) Append the current node's value to the list.
    d) Recursively call the helper function for the right child.
3) Call the helper function starting from the root node.
4) Initialize `min_diff` to infinity.
5) Iterate through the list of node values to find the minimum difference between consecutive values.
6) Return the minimum difference.
```

**⚠️ Common Mistakes**

- Forgetting to handle the case where the tree is empty or has only one node.
- Incorrectly calculating differences between non-consecutive nodes.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def inorder_traversal(root, nodes):
    if root is not None:
        inorder_traversal(root.left, nodes)
        nodes.append(root.val)
        inorder_traversal(root.right, nodes)

def min_diff_in_bst(root):
    nodes = []
    inorder_traversal(root, nodes)
    
    min_diff = float('inf')
    for i in range(1, len(nodes)):
        min_diff = min(min_diff, nodes[i] - nodes[i - 1])
        
    return min_diff
```
 
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with an input to check for the expected output
- Catch possible edge cases and off-by-one errors
- For a starting point, try checking your code against the Happy/Edge Case(s) above

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

Assume `N` represents the number of nodes in the BST.

* **Time Complexity**: `O(N)` because we need to traverse all the nodes in the tree.
* **Space Complexity**: `O(N)` for storing the node values during the inorder traversal.