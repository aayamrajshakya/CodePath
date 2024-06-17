*[[Unit 6 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 25 mins
* 🛠️ **Topics**: Linked Lists, Cycle Removal
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: How should the function behave if the list is already acyclic?
  - A: If there is no cycle, the function should return the list as is.

```markdown
HAPPY CASE
Input: 1 -> 2 -> 3 -> 4 -> 2 (Cycle starts at 2)
Output: 1 -> 2 -> 3 -> 4
Explanation: The cycle is removed and the list ends at node 4.

EDGE CASE
Input: 1 -> 2 -> 3 -> 4 -> 5 (No cycle)
Output: 1 -> 2 -> 3 -> 4 -> 5
Explanation: The list remains unchanged as there was no cycle to remove.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem involves detecting and removing cycles from a linked list, typically approached using Floyd's Cycle Detection Algorithm (Tortoise and Hare).

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use fast and slow pointers to detect a cycle, and then remove it by finding the start of the cycle and setting the last node's next to null.

```markdown
1) Use two pointers, slow and fast, to detect a cycle.
2) If a cycle is detected, find the starting point by resetting one pointer to the head and moving both at the same speed.
3) Traverse the cycle again to find the last node and set its next to null.
4) Return the head of the now acyclic list.
```

**⚠️ Common Mistakes**

- Failing to check for a null list or a list with only one element which cannot have a cycle.
- Incorrectly identifying the last node before the start of the cycle.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def detect_and_remove_cycle(head):
    if not head or not head.next:
        return head

    slow = fast = head
    has_cycle = False

    # Phase 1: Detecting the cycle using the Floyd's Cycle Detection Algorithm
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
        if slow == fast:
            has_cycle = True
            break

    # If there's no cycle, we can safely return as the list is already fine
    if not has_cycle:
        return head

    # Phase 2: Identifying the start of the cycle
    slow = head
    while slow != fast:
        slow = slow.next
        fast = fast.next

    # Phase 3: Remove the cycle by setting the `next` of the last node in the cycle to None
    # To find the last node in the cycle, continue from 'fast' until you reach 'slow' again
    while fast.next != slow:
        fast = fast.next

    fast.next = None  # Removing the cycle
    return head
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Test with lists that have and do not have cycles to ensure correct detection and removal.
- Verify that lists remain intact when no cycle exists.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(N)` as it may require traversing the entire list multiple times, once to detect the cycle and another time to find the junction.
* **Space Complexity**: `O(1)` because the space used does not scale with the input size, just pointers are moved.
