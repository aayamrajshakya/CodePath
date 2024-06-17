*[[Unit 9 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Hard
* ⏰ **Time to complete**: 30+ mins
* 🛠️ **Topics**: Tree, Recursion, Tree Traversal
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Can the trees be empty?
    - Yes, both trees can be empty. Two empty trees are considered the same.

- Can a tree have a different structure but still be transformable?
    - Yes.

```
HAPPY CASE
 
  1 (root1)
 / \
2   3

  1 (root2)
 / \
3   2

Input: root1, root2
Output: True
Explanation: We can swap the left and right children of the root node in root1 to get root2.
```
```
EDGE CASE

  1 (root1)
 /
2

  1 (root2)
   \
    2

Input: root1, root2
Output: False
Explanation: The structures are different as one tree has a left child and the other has a right child.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

For Tree problems, we want to consider the following approaches:

- Recursion: Useful for comparing nodes and their children.
- Tree Traversal: Exploring nodes and their children for comparisons.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use a recursive function to compare the nodes of the two trees. At each step, check if the children are the same or swapped.

```
1) Define a helper function `can_swap(root1, root2)` to compare nodes.
    a) If both nodes are None, return True.
    b) If only one of the nodes is None or their values are different, return False.
    c) Recursively check if the left and right children are the same or swapped.
2) In the main function `can_transform(root1, root2)`, call the helper function to start the comparison from the root nodes.
```

**⚠️ Common Mistakes**

- Forgetting to handle the case where both trees are empty.
- Incorrectly checking for swapped children.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

def can_swap(root1, root2):
    if not root1 and not root2:
        return True
    if not root1 or not root2 or root1.val != root2.val:
        return False
    
    # Check if children are the same or swapped
    return (can_swap(root1.left, root2.left) and can_swap(root1.right, root2.right)) or \
           (can_swap(root1.left, root2.right) and can_swap(root1.right, root2.left))

def can_transform(root1, root2):
    return can_swap(root1, root2)
```
 
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with an input to check for the expected output
- Catch possible edge cases and off-by-one errors
- For a starting point, try checking your code against the Happy/Edge Case(s) above

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

Assume `N` represents the number of nodes in the trees.

* **Time Complexity**: `O(N)` because we need to compare all nodes in the trees.
* **Space Complexity**: `O(N)` for the recursion stack in the worst case when the trees are completely unbalanced."