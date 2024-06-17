*[[Unit 9 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 30+ mins
* 🛠️ **Topics**: Tree, Breadth-First Search, Queue, Level Order Traversal
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Can the tree be empty?
    - Yes, if the tree is empty, return 0.

- How should we treat the root node's level?
    - The root node is at level 1 (odd).

```
HAPPY CASE

      1 (root)
     / \
    2   3
   / \ / \
  4  5 6  7

Input: root
Output: 18
Explanation: 
- Odd level nodes: 1 + 4 + 5 + 6 + 7 = 23
- Even level nodes: 2 + 3 = 5
- Difference: 23 - 5 = 18
```
```
EDGE CASE

    1 (root)

Input: root
Output: 1
Explanation: The tree has only one node which is at level 1, so the difference is 1.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

For Tree problems, we want to consider the following approaches:

- Breadth-First Search (BFS): Useful for level order traversal.
- Queue: Used to manage the order of node exploration.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use a BFS approach to traverse the tree level by level. Use a queue to keep track of nodes and their levels. Maintain two sums for odd and even levels and compute their difference at the end.

```
1) If the tree is empty, return 0.
2) Create an empty queue and add the root node with level 1.
3) Initialize sums for odd and even levels to 0.
4) While the queue is not empty:
    a) Get the number of nodes at the current level.
    b) For each node at the current level:
        i) Pop the node from the queue.
        ii) Add its value to the appropriate sum (odd or even) based on the current level.
        iii) Add the left and right children to the queue for the next level.
    c) Increment the level.
5) Return the difference between the odd and even sums.
```

**⚠️ Common Mistakes**

- Forgetting to handle the case where the tree is empty.
- Not correctly managing the queue for BFS.
- Incorrectly identifying the level of nodes.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
from collections import deque

class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

def level_difference(root):
    if not root:
        return 0
    
    queue = deque([root])
    level = 1
    odd_sum = 0
    even_sum = 0
    
    while queue:
        level_size = len(queue)
        
        for _ in range(level_size):
            node = queue.popleft()
            
            if level % 2 == 1:
                odd_sum += node.val
            else:
                even_sum += node.val
            
            if node.left:
                queue.append(node.left)
            if node.right:
                queue.append(node.right)
        
        level += 1
    
    return odd_sum - even_sum
```
 
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with an input to check for the expected output
- Catch possible edge cases and off-by-one errors
- For a starting point, try checking your code against the Happy/Edge Case(s) above

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

### Time Complexity: 
- **`O(N)`**, because we need to traverse all nodes in the tree.

### Space Complexity:
- **`O(N)`**, because of the queue that stores nodes at each level during traversal.