*[[Unit 9 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 30+ mins
* 🛠️ **Topics**: Tree, Depth-First Search, Recursion
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- What should be returned if the tree only contains one unique value?
    - Return -1.

- Are the node values guaranteed to be non-negative?
    - Yes, all node values are non-negative.

```
HAPPY CASE
    2
   / \
  2   5
     / \
    5   7

Input: root
Output: 5
Explanation: The second minimum value in the tree is 5.
```
```
EDGE CASE

    2 (root)
   / \
  2   2

Input: root
Output: -1
Explanation: All values in the tree are the same, so there is no second minimum value.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

For Tree problems, we want to consider the following approaches:

- Depth-First Search (DFS): Useful for traversing the tree and comparing node values.
- Tree Traversal: Exploring all nodes in the tree to find the second minimum value.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use a DFS approach to traverse the tree. Keep track of the smallest and the second smallest unique values encountered during the traversal.

```
1) Define a helper function `traverse(node, first_min, second_min)` to perform DFS.
    a) If the current node is None, return.
    b) If the current node's value is greater than `first_min` and less than `second_min`, update `second_min`.
    c) Recursively call the helper function for the left and right children.
2) In the main function `find_second_minimum_value(root)`, initialize `first_min` to the root's value and `second_min` to infinity.
3) Call the helper function to start the DFS from the root.
4) If `second_min` is still infinity after the traversal, return -1.
5) Otherwise, return `second_min`.
```

**⚠️ Common Mistakes**

- Forgetting to handle the case where all node values are the same.
- Not correctly updating the second minimum value.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
class TreeNode:
    def __init__(self, val, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

def traverse(node, first_min, second_min):
    if node:
        if first_min < node.val < second_min[0]:
            second_min[0] = node.val
        traverse(node.left, first_min, second_min)
        traverse(node.right, first_min, second_min)

def find_second_minimum_value(root):
    if not root or not root.left or not root.right:
        return -1

    # Set the initial minimum to the root's value
    first_min = root.val
    second_min = [float('inf')]

    traverse(root, first_min, second_min)

    # If we didn't find any value greater than first_min, return -1
    return second_min[0] if second_min[0] < float('inf') else -1
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