*[[Unit 9 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 20+ mins
* 🛠️ **Topics**: Tree, Breadth-First Search, Queue, Level Order Traversal
    
## 1: U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Can the tree be empty?
    - Yes, if the tree is empty, do not print anything.

- What should be printed if the tree has only one node?
    - Print the value of that single node.

```
HAPPY CASE
 
      1 (root)
     / \
    2   3
   / \ / \
  4  5 6  7

Input: root
Output: 1 2 3 4 7
Explanation: The first and last node of each level are printed. 
  1 is the only node at level 1, so it is both the first and last node. 
  2 and 3 are the first and last nodes at level 2.
  4 and 7 are the first and last nodes at level 3.
```
```
EDGE CASE
Input: None (root)
Output: (no output, as the tree is empty)
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g., Linked List or Dynamic Programming, and strategies or patterns in those categories.

For Tree problems, we want to consider the following approaches:

- Breadth-First Search (BFS): Useful for level order traversal while tracking the nodes in each level.
- Queue: Used to manage the order of node exploration.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use a BFS approach to traverse the tree level by level. Use a queue to keep track of nodes to be explored. Print the value of the first and last node at each level.

```
1) If the tree is empty, do not print anything.
2) Create an empty queue and add the root node.
3) While the queue is not empty:
    a) Get the number of nodes at the current level.
    b) For each node at the current level:
        i) Pop the node from the queue.
        ii) Print the node's value if it is the first or last node in the level.
        iii) Add the left child to the queue if it exists.
        iv) Add the right child to the queue if it exists.
```

**⚠️ Common Mistakes**

- Forgetting to handle the case where the tree is empty.
- Not correctly managing the queue for BFS.
- Incorrectly identifying and printing the first and last nodes of each level.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
from collections import deque

class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

def print_corners(root):
    if not root:
        return
    
    queue = deque()
    queue.append(root)
    
    while queue:
        level_size = len(queue)
        
        for i in range(level_size):
            node = queue.popleft()
            
            # Print the first and last node of the level
            if i == 0 or i == level_size - 1:
                print(node.val)
            
            if node.left:
                queue.append(node.left)
            if node.right:
                queue.append(node.right)
                
# Time complexity: O(n) where n is the number of nodes in the tree.
# To find the first and last node in each level, we must traverse each node in the tree.
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
- This is because we must visit each node exactly once to find the first and last nodes of each level.

### Space Complexity:
- **O(N)**, where N is the number of nodes in the tree.
- This is because the queue could hold up to N nodes in the worst case (when the tree is completely unbalanced).