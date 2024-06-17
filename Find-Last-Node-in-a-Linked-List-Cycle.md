*[[Unit 6 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 20 mins
* 🛠️ **Topics**: Linked Lists, Cycle Detection
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What if the linked list has no cycle?
  - Return None as there is no last node in the cycle.

```markdown
HAPPY CASE
Input: A list with a cycle (e.g., 1 -> 2 -> 3 -> 4 -> 5 -> 2)
Output: Node with value 5 (last node before the cycle starts again at node 2)
Explanation: The cycle occurs starting at node 2 and ends at node 5 which points back to node 2.

EDGE CASE
Input: A list with no cycle (e.g., 1 -> 2 -> 3 -> 4 -> 5)
Output: None
Explanation: There is no cycle in the list so there is no "last node in the cycle".
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

For problems involving cycles in linked lists, the Floyd’s Cycle Detection Algorithm is typically employed to find the presence of a cycle and the starting node of the cycle.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use Floyd's Cycle Detection to first find the cycle, then locate the last node in the cycle.

```markdown
1) Use two pointers (slow and fast) to detect a cycle using Floyd's algorithm.
2) If a cycle is detected, reset one pointer to head and find the starting node of the cycle.
3) Traverse the cycle to find the last node before it starts again.
```

**⚠️ Common Mistakes**

- Assuming the list has a cycle without verifying.
- Not considering the list without a tail (single node pointing to itself).

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def find_last_node_in_cycle(head):
    if not head or not head.next:
        return None

    slow = fast = head
    has_cycle = False

    # Phase 1: Detecting the cycle using the Floyd's Cycle Detection Algorithm
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
        if slow == fast:
            has_cycle = True
            break

    # If there's no cycle, return None
    if not has_cycle:
        return None

    # Phase 2: Identifying the start of the cycle
    slow = head
    while slow != fast:
        slow = slow.next
        fast = fast.next

    # Find the last node in the cycle
    cycle_start = slow
    last_node = cycle_start
    while last_node.next != cycle_start:
        last_node = last_node.next

    return last_node
```
  
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through the code with a known cycle to confirm detection and correct identification of the last node.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(N)` where `N` is the number of nodes. Both detection and finding the last node require traversal but do not exceed linear time.
* **Space Complexity**: `O(1)` as the space used does not scale with the size of the input.
