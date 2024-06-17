*[[Unit 10 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 30 mins
* 🛠️ **Topics**: Linked List, Circular List
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- What should be returned if the list is empty?
    - Create a new node with `insert_val` and point it to itself, then return this node.

```
HAPPY CASE
Input: start_node = [3, 4, 1], insert_val = 2
Output: [1, 2, 3, 4]
Explanation: The value 2 can be inserted between 1 and 3.

HAPPY CASE
Input: start_node = [1, 3, 5], insert_val = 2
Output: [1, 2, 3, 5]
Explanation: The value 2 can be inserted between 1 and 3.

EDGE CASE
Input: start_node = None, insert_val = 1
Output: [1]
Explanation: The list is empty, so create a new node with the value 1 pointing to itself.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

For Linked List problems, we want to consider the following approaches:

- Traversing the circular linked list to find the correct insertion point.
- Handling edge cases where the list is empty.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Traverse the circular linked list to find the appropriate insertion point based on the value to be inserted. Handle cases where the list is empty or all nodes have the same value.

```
1) If start_node is None:
    a) Create a new node with insert_val.
    b) Point the new node to itself.
    c) Return the new node.
2) Initialize prev to start_node and curr to start_node.next.
3) Traverse the circular linked list:
    a) Check if insert_val should be inserted between prev and curr.
    b) If insert_val is greater than prev and less than curr, or prev is greater than curr and insert_val is greater than prev or less than curr, insert the new node.
4) If we traverse the entire list without finding an insertion point, it means all nodes have the same value.
    a) Insert the new node at the end.
5) Return the start_node.
```

**⚠️ Common Mistakes**

- Not correctly handling the circular nature of the list.
- Not considering the case where the list is empty.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```
class Node:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

def insert(start_node, insert_val):
    if start_node is None:
        new_node = Node(insert_val)
        new_node.next = new_node
        return new_node

    prev, curr = start_node, start_node.next
    to_insert = False

    while True:
        if prev.val <= insert_val <= curr.val:
            # Case 1: Insert in the middle of the list.
            to_insert = True
        elif prev.val > curr.val:
            # Case 2: Insert at the boundary of the max and min values.
            if insert_val >= prev.val or insert_val <= curr.val:
                to_insert = True
        
        if to_insert:
            prev.next = Node(insert_val, curr)
            return start_node
        
        prev, curr = curr, curr.next
        if prev == start_node:
            break
    
    # Case 3: All nodes have the same value or we wrapped around without inserting.
    prev.next = Node(insert_val, curr)
    return start_node
```
 
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with an input to check for the expected output.
- Example: Trace with start_node = [3, 4, 1], insert_val = 2
    - Insert 2 between 1 and 3
    - Traverse the list to check if the order is maintained

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

Assume `N` represents the number of nodes in the circular linked list.

* **Time Complexity**: `O(N)` because we might need to traverse the entire list.
* **Space Complexity**: `O(1)` because we only use a constant amount of extra space.