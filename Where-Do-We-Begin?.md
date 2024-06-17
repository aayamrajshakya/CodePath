*[[Unit 6 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 15 mins
* 🛠️ **Topics**: Linked List, Cycle Detection, Two-Pointer Technique
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: How should the function behave when the linked list is empty?
    - A: The function should return `None`, as there is no cycle possible in an empty list.

```markdown
HAPPY CASE
Input: Create a linked list with nodes 1 -> 2 -> 3 -> 4 -> 2 (cycle starts back at 2)
Output: Node with value 2
Explanation: The cycle is detected, and the start of the cycle is correctly identified at node with value 2.

EDGE CASE
Input: head = None
Output: None
Explanation: An empty list has no nodes, hence no cycles.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g., Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem involves cycle detection in a linked list, which is a typical application of the slow-fast pointer technique. Identifying the start of the cycle post-detection involves an additional traversal, confirming the theory of two-pointer technique.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use the fast and slow pointers to detect a cycle, and once detected, use another pointer from the head to meet with the slow pointer to find the start of the cycle.

```markdown
1) Initialize two pointers, `slow` and `fast`, both at the head.
2) Move `slow` by one step and `fast` by two steps in a loop until they either meet or `fast` encounters a null (indicating no cycle).
3) If a cycle is detected (slow meets fast), use another pointer starting from the head and move both this new pointer and `slow` one step at a time until they meet.
4) The meeting point is the start of the cycle. Return this node.
5) If no cycle is detected, return `None`.
```

**⚠️ Common Mistakes**

- Incorrect handling of the cycle detection condition.
- Not correctly implementing the loop to find the start of the cycle.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
class Node:
    def __init__(self, value=None, next=None):
        self.value = value
        self.next = next

def find_loop_start(meet_point, head):
    slow2 = head
    while slow2 != meet_point:
        slow2 = slow2.next
        meet_point = meet_point.next
    return slow2

def get_loop_start(head):
    slow = fast = head
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
        if slow == fast:
            # A loop has been detected, find its start
            return find_loop_start(slow, head)
    return None # No loop found
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Validate the function with a list having a cycle and another without a cycle.
- Check for correctness in both odd and even-length cycles.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(n)` where `n` is the number of nodes before the cycle starts plus the cycle's length itself. The slow and fast pointers traverse the list, with fast covering twice the ground. However, both pointers will traverse at most `2n` steps in total (including the steps to find the start of the cycle).
* **Space Complexity**: `O(1)` because the space used does not scale with the size of the input. Only a fixed number of node pointers are used regardless of the list size.

