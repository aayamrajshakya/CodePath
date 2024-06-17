*[[Unit 6 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 20 mins
* 🛠️ **Topics**: Linked Lists, Cycle Detection
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: What if there is no cycle?
  - A: Return an empty list.

```markdown
HAPPY CASE
Input: 1 -> 2 -> 3 -> 4 -> 2 (Cycle starting at 2)
Output: [2, 3, 4]
Explanation: The cycle consists of the nodes starting from 2 to 4 and back to 2.

EDGE CASE
Input: 1 -> 2 -> 3 -> 4 -> 5 (No cycle)
Output: []
Explanation: There is no cycle, so the output is an empty list.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This is a classic problem of cycle detection in a linked list, specifically identifying the nodes that make up the cycle.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Detect a cycle using the two-pointer technique (Floyd's Cycle Detection), then identify and collect the cycle nodes.

```markdown
1) Start with two pointers, slow and fast, to detect a cycle.
2) If a cycle is detected, find the start of the cycle.
3) Traverse the cycle, collecting node values until the start is reached again.
4) Return the list of cycle nodes.
```

**⚠️ Common Mistakes**

- Not handling the case where there is no cycle correctly, leading to an incorrect return value.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def collect_cycle_nodes(head):
    if not head or not head.next:
        return []

    slow = fast = head
    has_cycle = False

    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
        if slow == fast:
            has_cycle = True
            break

    if not has_cycle:
        return []

    slow = head
    while slow != fast:
        slow = slow.next
        fast = fast.next

    cycle_nodes = []
    start_cycle = slow
    current = start_cycle
    while True:
        cycle_nodes.append(current.value)
        current = current.next
        if current == start_cycle:
            break

    return cycle_nodes
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace the code with a cycle to verify that all cycle nodes are collected.
- Check the edge case of no cycle to ensure the empty list is returned.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(N)` because detecting the cycle and collecting nodes both traverse parts of the list.
* **Space Complexity**: `O(k)` where `k` is the number of nodes in the cycle, needed for storing the cycle nodes.
