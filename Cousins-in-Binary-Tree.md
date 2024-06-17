*[[Unit 9 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 30+ mins
* 🛠️ **Topics**: Tree, Breadth-First Search, Queue
    
## 1: U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Can the tree be empty?
    - Yes, if the tree is empty, return False.

- What should be returned if the tree has only one node?
    - Return False, as a single node cannot have any cousins.

```
HAPPY CASE 1

      1 (root)
     / \
    2   3
   / 
  4  

Input: root, x = 4, y = 3
Output: False
Explanation: Node 4 is at depth 2 with parent 2, and Node 3 is at depth 1 with parent 1, so they are not cousins.
```
```
HAPPY CASE 2

    1 (root)
   / \
  2   3
   \   \
    4   5

Input: root, x = 4, y = 5
Output: True
Explanation: Node 4 and Node 5 are at the same depth 2 but with different parents 2 and 3, so they are cousins.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g., Linked List or Dynamic Programming, and strategies or patterns in those categories.

For Tree problems, we want to consider the following approaches:

- Breadth-First Search (BFS): Useful for level order traversal while tracking the nodes and their depths.
- Queue: Used to manage the order of node exploration.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use a BFS approach to traverse the tree level by level. Use a queue to keep track of nodes to be explored along with their corresponding parents and depths. Check if the two target nodes are found at the same depth with different parents.

```
1) If the tree is empty, return False.
2) Create a queue to hold the nodes, their parents, and their depths.
3) Initialize variables to store information about the nodes x and y.
4) While the queue is not empty:
    a) Pop the next node, its parent, and its depth from the queue.
    b) If the node's value is x or y, store its parent and depth.
    c) If both nodes' information is found, break the loop.
    d) Enqueue the left and right children with their parents and depths.
5) Check if both nodes have the same depth and different parents.
6) Return True if they are cousins, otherwise return False.
```

**⚠️ Common Mistakes**

- Forgetting to handle the case where the tree is empty.
- Not correctly managing the queue for BFS.
- Incorrectly identifying the nodes' parents and depths.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
from collections import deque

class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

def is_cousins(root, x, y):
    if not root:
        return False

    queue = deque()
    queue.append((root, None, 0))  # (node, parent, depth)
    x_info = y_info = None
    
    while queue:
        node, parent, depth = queue.popleft()
        
        if node.val == x:
            x_info = (parent, depth)
        if node.val == y:
            y_info = (parent, depth)
        
        if x_info and y_info:
            break
        
        if node.left:
            queue.append((node.left, node, depth + 1))
        if node.right:
            queue.append((node.right, node, depth + 1))
    
    if x_info and y_info:
        return x_info[1] == y_info[1] and x_info[0] != y_info[0]
    return False
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
- This is because we must visit each node exactly once to gather the necessary information.

### Space Complexity:
- **O(N)**, where N is the number of nodes in the tree.
- This is because the queue could hold up to N nodes in the worst case (when the tree is completely unbalanced).