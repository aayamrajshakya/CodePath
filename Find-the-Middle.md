*[[Unit 6 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 5 mins
* 🛠️ **Topics**: Linked List, Two Pointers
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: How should the function behave when the linked list contains an even number of nodes?
    - A: The function should return the second middle node as per the problem's instructions.

```markdown
HAPPY CASE
Input: head = Node(1, Node(2, Node(3, Node(4, Node(5)))))
Output: Node with value 3
Explanation: The middle node in an odd-numbered list is the third node.

EDGE CASE
Input: head = Node(1, Node(2, Node(3, Node(4))))
Output: Node with value 3
Explanation: In a list with an even number of nodes (4), the second middle node (the third node) is returned.
```
 
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This is a typical application of the slow-fast pointer technique to identify the middle of a singly linked list, which helps in scenarios like this where the list's length isn't known in advance or requires efficient access to middle elements.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use two pointers, where one moves at half the speed of the other, to efficiently find the middle of the list.

```markdown
1) Initialize both `slow` and `fast` pointers at the head of the linked list.
2) Move `slow` by one step and `fast` by two steps until `fast` reaches the end of the list or the last node.
3) When `fast` reaches the end, `slow` will be at the middle of the list.
4) Return the node pointed to by `slow`.
```

**⚠️ Common Mistakes**

- Incorrect loop condition that could skip the middle node or cause a null pointer error.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
class Node:
    def __init__(self, value=None, next=None):
        self.value = value
        self.next = next

def find_middle_element(head):
    slow = fast = head
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
    return slow
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Validate the function against a test suite that includes lists of varying lengths.
- Ensure it correctly handles the edge case of an even-length list by returning the second middle node.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(n)` where `n` is the number of nodes in the linked list. The slow pointer travels half the length of the list while the fast pointer might travel the entire length, but only once.
* **Space Complexity**: `O(1)` because the space used does not scale with the size of the input. Only two pointers are utilized regardless of the list size.

