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
Output: [3, 9, 20, 15, 7]
Explanation: The level order traversal of the tree is [3, 9, 20, 15, 7].
```
```
EDGE CASE
Input: None
Output: []
Explanation: The tree is empty, so return an empty list.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

For Tree problems, we want to consider the following approaches:

- Breadth-First Search (BFS): Useful for level order traversal.
- Queue: Used to manage the order of node exploration.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use a BFS approach to traverse the tree level by level. Use a queue to keep track of nodes to be explored, and a list to store the values of the nodes in the order they are visited.

```
1) If the tree is empty, return an empty list.
2) Create an empty queue and an empty list to store the explored nodes.
3) Add the root to the queue.
4) While the queue is not empty:
    a) Pop the next node off the queue (from the left side).
    b) Add the popped node's value to the list of explored nodes.
    c) Add each of the popped node's children to the end of the queue.
5) Return the list of visited nodes.
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

def level_order(root):
    # if the tree is empty
    if root is None:
        # return an empty list
        return []
    
    # create a new empty queue
    queue = deque()
    # create a list of nodes we have already explored
    visited = []

    # append the root of the tree to the queue
    queue.append(root)

    # while there are still nodes to explore
    while queue:
        # pop next node off the queue
        current_node = queue.popleft()

        # add the root to list of visited nodes
        visited.append(current_node.val)

        # if the current node has a left child
        if current_node.left is not None:
            # add the left child to the queue
            queue.append(current_node.left)

        # if the current node has a right child
        if current_node.right is not None:
            # add the right child to the queue
            queue.append(current_node.right)

    # return the list of visited nodes
    return visited
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
- This is because we need to visit each node exactly once.

### Space Complexity:
- **O(N)**, where N is the number of nodes in the tree.
- This is because the queue could hold up to N nodes in the worst case (when the tree is completely unbalanced)."