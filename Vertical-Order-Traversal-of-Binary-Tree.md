*[[Unit 9 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 30+ mins
* 🛠️ **Topics**: Tree, Breadth-First Search, Queue, HashMap
    
## 1: U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Can the tree be empty?
    - Yes, if the tree is empty, return an empty list.

- What should be returned if the tree has only one node?
    - Return a list with a single list containing that node's value.

```
HAPPY CASE
 
    3 (root)
   / \
  9   20
     /  \
    15   7

Input: root
Output: [[9], [3, 15], [20], [7]]
Explanation: The vertical order traversal of the tree is [9], [3, 15], [20], [7].
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

- Breadth-First Search (BFS): Useful for level order traversal while tracking the vertical columns.
- Queue: Used to manage the order of node exploration.
- HashMap (Dictionary): Used to store nodes by their vertical columns.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use a BFS approach to traverse the tree level by level. Use a dictionary to keep track of nodes at each vertical column and a queue to keep track of nodes to be explored along with their corresponding column indices.

```
1) If the tree is empty, return an empty list.
2) Create a dictionary to hold the nodes at each column index.
3) Create an empty queue and add the root node with column index 0.
4) While the queue is not empty:
    a) Pop the next node and its column index from the queue.
    b) If the node is not None, add its value to the dictionary at the corresponding column index.
    c) Enqueue the left child with column index - 1.
    d) Enqueue the right child with column index + 1.
5) Sort the dictionary keys (column indices) and extract the values in the sorted order.
6) Return the list of values.
```

**⚠️ Common Mistakes**

- Forgetting to handle the case where the tree is empty.
- Not correctly managing the queue for BFS.
- Incorrectly updating the dictionary for each column index.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
from collections import deque

class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

def vertical_order(root):
    if not root:
        return []

    # Dictionary to hold the nodes at each column index
    column_table = {}
    # Queue to hold the nodes and their respective column indices
    queue = deque()
    queue.append((root, 0))
    
    while queue:
        node, column = queue.popleft()
        
        if node is not None:
            if column not in column_table:
                column_table[column] = []
            column_table[column].append(node.val)
            
            # Enqueue left child with column - 1
            queue.append((node.left, column - 1))
            # Enqueue right child with column + 1
            queue.append((node.right, column + 1))
    
    # Sort the dictionary by column index and extract the values
    sorted_columns = sorted(column_table.keys())
    result = []
    for col in sorted_columns:
        result.append(column_table[col])
    
    return result
```

## 5: R-e-view

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with an input to check for the expected output
- Catch possible edge cases and off-by-one errors
- For a starting point, try checking your code against the Happy/Edge Case(s) above

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

### Time Complexity:
- **O(N log N)**, where N is the number of nodes in the tree.
- This is because we must visit each node exactly once and then sort the dictionary keys.

### Space Complexity:
- **O(N)**, where N is the number of nodes in the tree.
- This is because the queue and dictionary could hold up to N nodes in the worst case (when the tree is completely unbalanced).