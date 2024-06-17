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

- Should the new tree maintain the BST properties?
    - Yes, the new tree should maintain the properties of a BST with each node having no left child and only one right child.

- What should be returned if the tree is empty?
    - Return None.

```
HAPPY CASE

      5 (root)
     / \
    3   6
   / \   \
  2   4   8
 /       / \
1       7   9

Input: root
Output: 

  1 (root)
   \
    2
     \
      3
       \
        ...etc
         \
          9

Explanation: The new tree should be a right-skewed tree with nodes in increasing order.
```
```
EDGE CASE
Input: root = None
Output: None
Explanation: The tree is empty, so return None.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

For BST problems, we want to consider the following approaches:

- Inorder Traversal: Since an inorder traversal of a BST yields sorted node values, it is useful for rearranging nodes.
- Tree Reconstruction: Constructing a new tree based on sorted node values.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Perform an inorder traversal of the BST to get a sorted list of node values. Then, create a new tree where each node only has a right child using these sorted values.

```
1) Initialize an empty list to store node values.
2) Define a helper function `inorder_traversal(root, nodes)` to perform an inorder traversal.
    a) If the current node is None, return.
    b) Recursively call the helper function for the left child.
    c) Append the current node's value to the list.
    d) Recursively call the helper function for the right child.
3) Call the helper function starting from the root node.
4) Create a new root node with the first value from the list.
5) Iterate through the remaining values and add them as right children of the new tree.
6) Return the new root.
```

**⚠️ Common Mistakes**

- Forgetting to handle the case where the tree is empty.
- Incorrectly building the new tree structure.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

def inorder_traversal(root, nodes):
    if root:
        inorder_traversal(root.left, nodes)
        nodes.append(root.val)
        inorder_traversal(root.right, nodes)

def increasing_bst(root):
    nodes = []
    inorder_traversal(root, nodes)
    
    # Create a new root with the first value
    new_root = TreeNode(nodes[0])
    current = new_root
    
    # Add the rest of the values as right children
    for value in nodes[1:]:
        current.right = TreeNode(value)
        current = current.right
    
    return new_root
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
* **Space Complexity**: `O(N)` for storing the node values during the inorder traversal and constructing the new tree.