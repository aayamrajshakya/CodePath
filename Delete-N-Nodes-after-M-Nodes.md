*[[Unit 10 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 30 mins
* 🛠️ **Topics**: Linked List, Two Pointers
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- What should be returned if the linked list is empty?
    - None, since there are no nodes to modify.

```
HAPPY CASE
Input: head = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10], m = 2, n = 3
Output: [1, 2, 6, 7, 10]
Explanation: Keep the first 2 nodes, remove the next 3 nodes, and repeat.

HAPPY CASE
Input: head = [1, 2, 3, 4, 5], m = 1, n = 2
Output: [1, 4]
Explanation: Keep the first node, remove the next 2 nodes, and repeat.

EDGE CASE
Input: head = [], m = 2, n = 3
Output: []
Explanation: The list is empty, so the output is also empty.

EDGE CASE
Input: head = [1, 2, 3], m = 3, n = 1
Output: [1, 2, 3]
Explanation: There are no nodes to remove after the first 3 nodes.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

For Linked List problems, we want to consider the following approaches:

- Using two pointers to skip and delete nodes as required.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Traverse the linked list while keeping `m` nodes and removing `n` nodes. Use a pointer to track the current node and another to help in deletion.

```
1) Initialize the current pointer to the head of the list.
2) Traverse the list, keeping the first `m` nodes:
    a) Move the current pointer `m` steps forward.
3) Start the deletion process:
    a) Initialize a temporary pointer to the node after the current node.
    b) Move the temporary pointer `n` steps forward to skip `n` nodes.
4) Link the current node to the node after the `n` skipped nodes.
5) Move the current pointer to the node after the skipped nodes and repeat the process.
6) Return the modified head of the list.
```

**⚠️ Common Mistakes**

- Not correctly handling the case where there are fewer than `m` nodes left in the list.
- Not correctly handling the case where there are fewer than `n` nodes to delete.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```
class Node:
    def __init__(self, val=0, next=None):
        self.value = val
        self.next = next

def delete_nodes(head, m, n):
    current = head
    
    while current:
        # Skip m nodes
        for _ in range(1, m):
            if current is None:
                return head
            current = current.next
        
        # Start deletion process
        if current is None:
            return head
        
        # Delete next n nodes
        temp = current.next
        for _ in range(n):
            if temp is None:
                break
            temp = temp.next
        
        # Link the m-th node to the node after the n-th node
        current.next = temp
        current = temp
    
    return head
```
 
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with an input to check for the expected output.
- Example: Trace with head = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10], m = 2, n = 3
    - current = 1, skip 2 nodes -> 2
    - delete 3 nodes -> 6
    - current = 6, skip 2 nodes -> 7
    - delete 3 nodes -> 10
    - Return head

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

Assume `N` represents the number of nodes in the list.

* **Time Complexity**: `O(N)` because we need to traverse the list once.
* **Space Complexity**: `O(1)` because we only use a constant amount of extra space.