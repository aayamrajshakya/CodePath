*[[Unit 6 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 10 mins
* 🛠️ **Topics**: Linked List, Two-Pointer Technique
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: What should happen if the linked list is empty?
    - A: The function should return `False` since there is no node to match `val`.

```markdown
HAPPY CASE
Input: head = Node(1, Node(2, Node(3))), val = 2
Output: True
Explanation: The middle node in an odd-numbered list is 2, which matches `val`.

EDGE CASE
Input: head = Node(1, Node(2, Node(3, Node(4)))), val = 3
Output: True
Explanation: In a list with an even number of nodes, the second middle node is 3, which matches `val`.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g., Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem utilizes the slow-fast pointer technique, commonly used in problems involving linked lists to find middle elements or detect cycles.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use the slow-fast pointer technique to locate the middle or the second middle node in the list, and then compare its value to `val`.

```markdown
1) Check if the head is `None` and return `False` immediately, as there's no node to check against `val`.
2) Initialize both `slow` and `fast` pointers at the head.
3) Traverse the list: move `slow` by one step and `fast` by two steps until `fast` reaches the end or the last node.
4) At the end of the traversal, `slow` will point to the middle (or second middle) node.
5) Compare `slow.value` to `val` and return the result.
```

**⚠️ Common Mistakes**

- Not handling the case where the list is empty.
- Incorrect loop condition that doesn't properly account for the end of the list.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
class Node:
    def __init__(self, value=None, next=None):
        self.value = value
        self.next = next

def middle_match(head, val):
    if not head:
        return False  # Return False as there's no node to match with val

    slow = fast = head
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
    return slow.value == val  # Check if the middle node's value matches val
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Test with both odd and even number of nodes.
- Test with edge cases such as a single-node list or an empty list.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(n/2)` which simplifies to `O(n)` because in the worst case, the loop must execute while slow pointer travels through half of the list to reach the middle.
* **Space Complexity**: `O(1)` since no additional data structures are needed beyond the two pointers, slow and fast.

