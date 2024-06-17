*[[Unit 9 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 30+ mins
* 🛠️ **Topics**: Tree, Recursion, Tree Traversal
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Can the tree be empty?
    - Yes, if the tree is empty, return None.

- What should be done with the leaf nodes?
    - Leaf nodes should have their values replaced by 0 since they don't have any children.

```
HAPPY CASE

    1 (root)
   / \
  2   3
 / \
4   5

Input: root
Output: root

    14 (root)
   /  \
  9    0
 / \
0   0

Explanation: 
- Node with value 1: left subtree sum = 9, right subtree sum = 0, new value = 9
- Node with value 2: left subtree sum = 4, right subtree sum = 5, new value = 9
- Node with value 3: left subtree sum = 0, right subtree sum = 0, new value = 0
- Node with value 4: new value = 0
- Node with value 5: new value = 0
```
```
EDGE CASE

     1 (root)

Input: root
Output: root

     0 (root)

Explanation: The tree has only one node which is a leaf node, so its value is replaced by 0.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

For Tree problems, we want to consider the following approaches:

- Post-order Traversal: Useful for calculating the sum of subtrees before updating the current node.
- Recursion: Effective for traversing and updating the tree.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use a post-order traversal to first calculate the sum of all elements in the left and right subtrees, and then update the value of the current node to be this sum. Return the sum of the subtree including the node's original value.

```
1) Define a helper function `post_order(node)` to perform post-order traversal.
    a) If the current node is None, return 0.
    b) Recursively calculate the sum of the left subtree.
    c) Recursively calculate the sum of the right subtree.
    d) Update the current node's value to be the sum of the left and right subtree values.
    e) Return the sum of the current subtree including the original node's value.
2) In the main function `sum_transform(root)`, call the helper function to start the post-order traversal from the root.
3) Return the modified root.
```

**⚠️ Common Mistakes**

- Forgetting to handle the case where the tree is empty.
- Incorrectly updating the values of the nodes before calculating the subtree sums.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

def post_order(node):
    if not node:
        return 0
    
    # Recursively calculate the sum of the left and right subtrees
    left_sum = post_order(node.left)
    right_sum = post_order(node.right)
    
    # Update the current node's value to the sum of left and right subtree values
    original_value = node.val
    node.val = left_sum + right_sum
    
    # Return the sum of the current subtree including the original node's value
    return node.val + original_value

def sum_transform(root):
    post_order(root)
    return root
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
* **Space Complexity**: `O(N)` for the recursion stack in the worst case when the tree is completely unbalanced.