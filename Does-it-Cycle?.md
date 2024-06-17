*[[Unit 6 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 15 mins
* 🛠️ **Topics**: Linked List, Two Pointers, Cycle Detection
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: What happens if the linked list is empty or contains only one node without a cycle?
    - A: The function should return `False` as there is no cycle.

```markdown
HAPPY CASE
Input: head = Node(1, Node(2, Node(3, Node(1))))
Output: True
Explanation: The last node points back to the first node, creating a cycle.

EDGE CASE
Input: head = None
Output: False
Explanation: An empty list cannot contain a cycle.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem is a classic example of detecting cycles in a linked list, typically solved using the Floyd's Tortoise and Hare algorithm, which uses two pointers moving at different speeds.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Utilize two pointers, one slow and one fast, to traverse the list. If the fast pointer ever equals the slow pointer, a cycle is present.

```markdown
1) Initialize two pointers, both at the head of the list.
2) Move the slow pointer by one step and the fast pointer by two steps in each iteration.
3) If the fast pointer either becomes null or reaches the end of the list, return `False`.
4) If the slow pointer ever meets the fast pointer, return `True`.
```

**⚠️ Common Mistakes**

- Failing to check for the end of the list, which could lead to a null pointer exception.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def has_cycle(head):
    slow = fast = head
    while fast and fast.next:
        slow = slow.next          # move slow pointer by 1 step
        fast = fast.next.next     # move fast pointer by 2 steps
        if slow == fast:
            return True           # Cycle detected
    return False                  # No cycle detected
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Validate against both cyclic and acyclic lists.
- Ensure the function exits correctly when the list is empty or has one node.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

Assume `n` represents the number of nodes in the linked list.

* **Time Complexity**: `O(n)` because, in the worst-case scenario, the fast pointer might need to travel around the entire list once before meeting the slow pointer, assuming there is a cycle.
* **Space Complexity**: `O(1)` because no additional space is used regardless of the size of the input list.

