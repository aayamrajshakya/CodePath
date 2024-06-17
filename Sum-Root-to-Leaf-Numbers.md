*[[Unit 10 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 30 mins
* 🛠️ **Topics**: Tree, Depth-First Search (DFS)
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- What should be returned if the tree is empty?
    - 0, since there are no root-to-leaf paths.

```
HAPPY CASE
Input: root = [1, 2, 3]
Output: 25
Explanation: The root-to-leaf paths are 12 and 13, and their sum is 12 + 13 = 25.

HAPPY CASE
Input: root = [4, 9, 0, 5, 1]
Output: 1026
Explanation: The root-to-leaf paths are 495, 491, and 40, and their sum is 495 + 491 + 40 = 1026.

EDGE CASE
Input: root = []
Output: 0
Explanation: The tree is empty, so the sum of all root-to-leaf numbers is 0.

EDGE CASE
Input: root = [0, 1, 2]
Output: 12
Explanation: The root-to-leaf paths are 01 and 02, and their sum is 1 + 2 = 3.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

For Tree problems, we want to consider the following approaches:

- Depth-First Search (DFS) to traverse all root-to-leaf paths.
- Accumulate the number formed by the path from the root to each leaf node.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use DFS to traverse the tree. At each node, calculate the number formed by the path from the root to that node. If it's a leaf node, add the number to the total sum.

```
1) Define a helper function `dfs(node, current_number)` that:
    a) Returns 0 if the node is None.
    b) Updates `current_number` by appending the node's value.
    c) Returns `current_number` if the node is a leaf.
    d) Recursively calls `dfs` for the left and right children.
    e) Returns the sum of the results from the left and right subtrees.
2) Initialize the DFS with the root node and an initial `current_number` of 0.
3) Return the result of the DFS.
```

**⚠️ Common Mistakes**

- Not handling the case where the tree is empty.
- Incorrectly updating the `current_number` when traversing the tree.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```
class TreeNode(object):
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

def sum_numbers(root):
    def dfs(node, current_number):
        if node is None:
            return 0
        
        current_number = current_number * 10 + node.val
        
        # If the current node is a leaf, return the current number
        if node.left is None and node.right is None:
            return current_number
        
        # Recursively sum the numbers from the left and right subtrees
        left_sum = dfs(node.left, current_number)
        right_sum = dfs(node.right, current_number)
        
        return left_sum + right_sum
    
    # Start DFS with the root and initial current number as 0
    return dfs(root, 0)
```
 
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with an input to check for the expected output.
- Example: Trace with root = [1, 2, 3]
    - current_number = 1 at root
    - current_number = 12 at left child
    - current_number = 13 at right child
    - Sum = 12 + 13 = 25

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

Assume `N` represents the number of nodes in the tree.

* **Time Complexity**: `O(N)` because we need to visit each node once.
* **Space Complexity**: `O(H)` where `H` is the height of the tree, representing the space on the call stack due to recursion.