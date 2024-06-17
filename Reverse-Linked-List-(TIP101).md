*[[Unit 10 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 20 mins
* 🛠️ **Topics**: Linked List, Iteration
* 📺 **Non-TIP101 Version**: [[Reverse Linked List]]
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- What should be returned if the linked list is empty?
    - None, since there are no nodes to reverse.

```
HAPPY CASE
Input: head = [1, 2, 3, 4, 5]
Output: [5, 4, 3, 2, 1]
Explanation: The list is reversed to become [5, 4, 3, 2, 1].

HAPPY CASE
Input: head = [1]
Output: [1]
Explanation: The list has only one node, so the reversed list is the same.

EDGE CASE
Input: head = []
Output: None
Explanation: The list is empty, so the reversed list is also None.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

For Linked List problems, we want to consider the following approaches:

- Iterating through the linked list and reversing the pointers at each node.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Iterate through the linked list and reverse the pointers at each node. Use three pointers to track the previous, current, and next nodes.

```
1) Initialize previous to None (this will be the new head of the reversed list).
2) Initialize current to head (start with the head of the original list).
3) While current is not None:
    a) Store the next node in a temporary variable next_node.
    b) Reverse the current node's pointer by setting current.next to previous.
    c) Move the previous pointer to the current node.
    d) Move the current pointer to the next_node.
4) Return previous (this will be the new head of the reversed list).
```

**⚠️ Common Mistakes**

- Forgetting to handle the case where the linked list is empty.
- Incorrectly updating the pointers, leading to losing references to nodes.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```
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

- Trace through your code with an input to check for the expected output.
- Example: Trace with head = [1, 2, 3, 4, 5]
    - previous = None, current = 1
    - Reverse current.next to point to previous (None), move previous to 1, move current to 2
    - Continue until current is None
    - Return previous (5)

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

Assume `N` represents the number of nodes in the linked list.

* **Time Complexity**: `O(N)` because we need to traverse all nodes in the list.
* **Space Complexity**: `O(1)` because we only use a constant amount of extra space.