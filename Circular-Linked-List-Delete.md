*[[Unit 6 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 20 mins
* 🛠️ **Topics**: Circular Linked Lists, Deletion
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: What if the node with the value `val` does not exist in the list?
  - A: If the node does not exist, the list remains unchanged.

```markdown
HAPPY CASE
Input: 1 -> 2 -> 3 -> 1 (Circular), val = 2
Output: 1 -> 3 -> 1
Explanation: Node with value 2 is removed, list remains circular.

EDGE CASE
Input: 2 -> 2 (Circular, single node repeating), val = 2
Output: None
Explanation: Removing the node results in an empty list as it was the only node repeating.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This involves modifying a circular linked list to delete a specified node, which is a direct manipulation of node pointers within a circular structure.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Traverse the circular list to find the node with the given value and adjust pointers to exclude it from the list.

```markdown
1) If the list is empty or only one node that matches, handle these as special cases.
2) Traverse the list to find the node with the specified value.
3) Adjust the pointers of the preceding node to bypass the found node.
4) If the removed node was the head, update the head pointer accordingly.
5) Ensure the list remains circular unless emptied.
```

**⚠️ Common Mistakes**

- Not properly re-establishing the circular nature of the list after deletion.
- Overlooking the case where the target node might be the head of the list.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def delete_node(head, val):
    if not head:
        return None

    # Handle the case where the list might only have one node
    if head == head.next:
        if head.value == val:
            return None  # Delete the only node in the list
        else:
            return head  # The value does not match; no node is deleted

    # Start searching for the node to delete
    current = head
    prev = None
    while True:
        if current.value == val:
            if current == head:
                # If it's the head, we need to change the head and fix the tail
                # Find the tail (node before head)
                tail = head
                while tail.next != head:
                    tail = tail.next
                # Move head to next node
                head = head.next
                tail.next = head
            else:
                # If it's not the head, just adjust the previous node's next
                prev.next = current.next
            return head
        prev = current
        current = current.next
        # Since it's circular, stop if we have gone through the list once
        if current == head:
            break

    return head  # Return the possibly new head of the list
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Test with a list where the deletion node is at various positions, including the head, to ensure correct linkage.
- Validate the edge case where the list becomes empty after removal.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(n)` because in the worst case, the entire list might need to be traversed.
* **Space Complexity**: `O(1)` as no additional space is needed beyond a few temporary pointers.
