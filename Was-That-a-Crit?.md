*[[Unit 6 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 20 mins
* 🛠️ **Topics**: Linked List, Searching
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: What constitutes a local minima or maxima when consecutive values are equal?
    - A: If consecutive values are equal, the sequence should not count as a local maxima or minima since there isn’t a clear increase or decrease.

```markdown
HAPPY CASE
Input: head = Node(1, Node(2, Node(3, Node(4))))
Output: 2
Explanation: The local maxima are 2 and 3.

EDGE CASE
Input: head = Node(3, Node(3, Node(3)))
Output: 0
Explanation: No critical points as all values are the same.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g., Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem is akin to finding peaks and valleys in an array, but applied to a singly linked list.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Traverse the linked list, comparing each node with its predecessor and successor to identify local maxima and minima.

```markdown
1) Check if the list has fewer than three nodes. If so, return 0 as no critical points can exist.
2) Initialize pointers for the previous, current, and next nodes.
3) Loop through the list until `next_node` is `None`:
   - Check if `current` is greater or less than both `prev_node` and `next_node`.
   - If true, increment a counter.
   - Update pointers to move to the next set of nodes.
4) Return the counter of critical points.
```

**⚠️ Common Mistakes**

- Not handling lists with fewer than three nodes.
- Incorrectly counting nodes that are not true local maxima or minima due to consecutive duplicates.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def count_critical_points(head):
    if not head or not head.next or not head.next.next:
        return 0  # If there are less than three nodes, there can't be any critical points

    current = head.next
    prev_node = head
    next_node = current.next
    count = 0

    while next_node:
        if (current.value > prev_node.value and current.value > next_node.value) or \
           (current.value < prev_node.value and current.value < next_node.value):
            count += 1
        # Move to the next set of nodes
        prev_node = current
        current = next_node
        next_node = next_node.next

    return count
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Test with increasing, decreasing, and mixed value sequences.
- Confirm the function correctly ignores the head and tail nodes as potential critical points.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(n)` where `n` is the number of nodes in the linked list. The list is traversed once, examining each node in the context of its neighbors.
* **Space Complexity**: `O(1)` because the solution uses a constant amount of space regardless of the input size; only a few pointers and a counter variable are used.

