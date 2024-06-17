*[[Unit 6 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 10 mins
* 🛠️ **Topics**: Linked List, In-place Operations
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: Does the linked list handle different data types?
    - A: The function assumes the list contains comparable data types that support the operations used.

```markdown
HAPPY CASE
Input: head = Node(1, Node(2, Node(3)))
Output: 3 -> 2 -> 1
Explanation: Each node's pointer is reversed, resulting in the tail becoming the new head.

EDGE CASE
Input: head = None
Output: None
Explanation: An empty list remains empty when reversed.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

The problem of reversing a singly linked list in place is fundamental in manipulating data structures, especially linked lists.  There is no special trick to it, we will just need to carefully keep track of our pointers as we go.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Reverse the pointers of the list nodes one by one, moving from the head towards the tail.

```markdown
1) Initialize a pointer `previous` to `None` and start with `current` at the head of the list.
2) Iterate through the list, for each node:
    - Store the next node temporarily.
    - Reverse the `current.next` pointer to point to `previous`.
    - Move `previous` and `current` forward.
3) Return `previous` as it will be the new head of the reversed list after the loop completes.
```

**⚠️ Common Mistakes**

- Losing reference to the rest of the list while reversing pointers.
- Returning the wrong node as the head of the reversed list.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
class Node:
    def __init__(self, value=None, next=None):
        self.value = value
        self.next = next

def reverse(head):
    previous = None  # This will eventually become the new head of the reversed list
    current = head  # Start with the head of the original list

    while current:
        next_node = current.next  # Temporarily store the next node
        current.next = previous  # Reverse the current node's pointer
        previous = current  # Move pointers one position forward
        current = next_node  # Continue to next node

    return previous  # At the end, 'previous' will be the new head of the reversed list
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Test the function with varying lengths of lists, including the edge case of an empty list.
- Ensure that the function does not use extra space beyond the necessary pointers.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(n)` where `n` is the length of the linked list. Each node in the list is visited once to reverse its pointer.
* **Space Complexity**: `O(1)` because the space used is constant, involving only a few pointer variables, regardless of the size of the input list.

