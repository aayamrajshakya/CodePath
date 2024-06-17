*[[Unit 9 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 20+ mins
* 🛠️ **Topics**: Tree, Breadth-First Search, Queue
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Can the tree be empty?
    - Yes, if the tree is empty, return 0.

- What should be returned if the tree has only one node?
    - Return 1 as the minimum depth.

```
HAPPY CASE

    3 (root)
   / \
  9   20
     /  \
    15   7

Input: root
Output: 2
Explanation: The minimum depth path is [3, 9] with length 2.
```
```
EDGE CASE
Input: None
Output: 0
Explanation: The tree is empty, so return 0.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

For Tree problems, we want to consider the following approaches:

- Breadth-First Search (BFS): Useful for finding the shortest path in an unweighted tree.
- Queue: Used to manage the order of node exploration.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use a BFS approach to traverse the tree level by level. Use a queue to keep track of nodes and their depths. The first time a leaf node is encountered, return its depth.

```
1) If the tree is empty, return 0.
2) Create an empty queue and add the root node with depth 1.
3) While the queue is not empty:
    a) Pop the next node and its depth from the queue.
    b) If the node is a leaf, return its depth.
    c) Add the left and right children to the queue with their depths incremented by 1.
4) Return 0 (this line will never be reached if the input tree is valid).
```

**⚠️ Common Mistakes**

- Forgetting to handle the case where the tree is empty.
- Not correctly managing the queue for BFS.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
from collections import deque

class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

def min_depth(root):
    if not root:
        return 0
    
    queue = deque()  # The queue stores tuples of (node, depth)
    queue.append((root, 1))
    
    while queue:
        node, depth = queue.popleft()
        
        # Check if the current node is a leaf node
        if not node.left and not node.right:
            return depth
        
        # Add the left child to the queue if it exists
        if node.left:
            queue.append((node.left, depth + 1))
        
        # Add the right child to the queue if it exists
        if node.right:
            queue.append((node.right, depth + 1))
    
    return 0  # This line will never be reached if the input tree is valid
```
 
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with an input to check for the expected output
- Catch possible edge cases and off-by-one errors
- For a starting point, try checking your code against the Happy/Edge Case(s) above

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

### Time Complexity: 
- **O(N)**, where N is the number of nodes in the tree.
- This is because we must enqueue and dequeue each node exactly once to check the depth of each path.

### Space Complexity:
- **O(N)**, where N is the number of nodes in the tree.
- This is because the queue could hold up to N nodes in the worst case (when the tree is completely unbalanced).