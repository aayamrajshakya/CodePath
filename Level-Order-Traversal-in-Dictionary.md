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
    - Yes, if the tree is empty, return an empty dictionary.

- What should be returned if the tree has only one node?
    - Return a dictionary with one key-value pair: {1: [node.val]}.

```
HAPPY CASE

    3 (root)
   / \
  9   20
     /  \
    15   7

Input: root
Output: {1: [3], 2: [9, 20], 3: [15, 7]}
Explanation: The level order traversal of the tree is {1: [3], 2: [9, 20], 3: [15, 7]}.
```
```
EDGE CASE
Input: None
Output: {}
Explanation: The tree is empty, so return an empty dictionary.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g., Linked List or Dynamic Programming, and strategies or patterns in those categories.

For Tree problems, we want to consider the following approaches:

- Breadth-First Search (BFS): Useful for level order traversal while tracking the levels.
- Queue: Used to manage the order of node exploration.
- HashMap (Dictionary): Used to store nodes by their levels.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use a BFS approach to traverse the tree level by level. Use a dictionary to keep track of nodes at each level and a queue to keep track of nodes to be explored along with their corresponding levels.

```
1) If the tree is empty, return an empty dictionary.
2) Create a dictionary to hold the nodes at each level.
3) Create an empty queue and add the root node with level 1.
4) While the queue is not empty:
    a) Pop the next node and its level from the queue.
    b) If the level is not in the dictionary, add it.
    c) Add the node's value to the dictionary at the corresponding level.
    d) Enqueue the left child with level + 1.
    e) Enqueue the right child with level + 1.
5) Return the dictionary.
```

**⚠️ Common Mistakes**

- Forgetting to handle the case where the tree is empty.
- Not correctly managing the queue for BFS.
- Incorrectly updating the dictionary for each level.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
from collections import deque

class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

def level_dict(root):
    if not root:
        return {}
    
    result = {}
    queue = deque()
    queue.append((root, 1))  # The queue stores tuples of (node, level)
    
    while queue:
        node, level = queue.popleft()
        
        if level not in result:
            result[level] = []
        
        result[level].append(node.val)
        
        if node.left:
            queue.append((node.left, level + 1))
        if node.right:
            queue.append((node.right, level + 1))
    
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
- This is because the queue and dictionary could hold up to N nodes in the worst case (when the tree is completely unbalanced).