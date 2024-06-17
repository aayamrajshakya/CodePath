*[[Unit 6 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 15 mins
* 🛠️ **Topics**: Linked Lists, Cycle Detection
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: What if the list is empty or has only one node without a cycle?
    - A: The function should return 0 for no cycle.

```markdown
HAPPY CASE
Input: Head = A -> B -> C -> D -> E -> C (back to C)
Output: 3
Explanation: The cycle involves nodes C, D, and E.

EDGE CASE
Input: Head = A -> B -> C -> D -> None
Output: 0
Explanation: There is no cycle in this linked list.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

For cycle detection problems in linked lists, the Floyd's Cycle Detection Algorithm, also known as the "Tortoise and Hare" approach, is typically used.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use the two-pointer technique to detect the cycle and calculate its length.

```markdown
1) Initialize two pointers, `slow` and `fast`, at the head.
2) Move `slow` by one step and `fast` by two steps.
3) If `slow` and `fast` meet, a cycle exists.
4) To determine the cycle's length, continue moving `slow` one step at a time while counting the steps until it meets `fast` again.
```

**⚠️ Common Mistakes**

- Forgetting to check if the list is empty or has only one node, which should return 0 as there can be no cycle.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
#Helper function
def calculate_cycle_length(meet_point):
    current = meet_point.next
    length = 1
    while current != meet_point:
        current = current.next
        length += 1
    return length

def cycle_length(head):
    slow = fast = head
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
        if slow == fast:
            # A loop has been detected, calculate its length
            return calculate_cycle_length(slow)
    return 0  # No loop
```
  
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with an input to check for the expected output
- Catch possible edge cases and off-by-one errors

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

Assume `N` represents the total number of nodes in the linked list and `M` the length of the cycle.

* **Time Complexity**: `O(N)` because in the worst case, we traverse the list twice before finding the cycle.
* **Space Complexity**: `O(1)` because no additional storage is needed beyond the two pointers used for detection.
