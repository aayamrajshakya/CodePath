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
    - Yes, if the tree is empty, return an empty list.

- What should be returned if the tree has only one node?
    - Return a list with that single node's value.

```
HAPPY CASE

    3 (root)
   / \
  9   20
     /  \
    15   7

Input: root
Output: [3, 29, 22]
Explanation: The level sums are 3 for the first level, 29 for the second level, and 22 for the third level.
```
```
EDGE CASE
Input: None
Output: []
Explanation: The tree is empty, so return an empty list.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g., Linked List or Dynamic Programming, and strategies or patterns in those categories.

For Tree problems, we want to consider the following approaches:

- Breadth-First Search (BFS): Useful for level order traversal.
- Queue: Used to manage the order of node exploration.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use a BFS approach to traverse the tree level by level. Use a queue to keep track of nodes to be explored, and a list to store the sum of node values for each level.

```
1) If the tree is empty, return an empty list.
2) Create an empty queue and add the root node.
3) Create an empty list to store the result.
4) While the queue is not empty:
    a) Get the number of nodes at the current level.
    b) Initialize the sum for the current level to 0.
    c) For each node at the current level:
        i) Pop the node from the queue.
        ii) Add its value to the current level sum.
        iii) Add the left child to the queue if it exists.
        iv) Add the right child to the queue if it exists.
    d) Add the current level sum to the result list.
5) Return the result list.
```

**⚠️ Common Mistakes**

- Forgetting to handle the case where the tree is empty.
- Not correctly managing the queue for BFS.
- Incorrectly managing the sums for each level.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
from collections import deque

class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

def level_sum(root):
    if not root:
        return []
    
    queue = deque([root])
    result = []
    
    while queue:
        level_size = len(queue)
        level_sum = 0
        
        for i in range(level_size):
            node = queue.popleft()
            level_sum += node.val
            
            if node.left:
                queue.append(node.left)
            if node.right:
                queue.append(node.right)
        
        result.append(level_sum)
    
    return result
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
- This is because we must visit each node exactly once.

### Space Complexity:
- **O(N)**, where N is the number of nodes in the tree.
- This is because the queue could hold up to N nodes in the worst case (when the tree is completely unbalanced).