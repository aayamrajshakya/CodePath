*[[Unit 5 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What should the function do if the index `i` is not within the bounds of the list?
  - If `i` is out of bounds, the function should return the list unchanged, ensuring no removal occurs for non-existent indices.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Traverse the linked list to the node at index `i`, remove that node by updating the `next` pointer of the node before it, and return the possibly updated head of the list.

```markdown
1) If the index is negative or the list is empty, return the head unmodified.
2) If the node to be removed is the head (i.e., `i == 0`), adjust the head to the next node.
3) For other indices, iterate through the list with a counter until reaching the node just before the target index.
4) If the target node (`i`) is found (i.e., `count == i` and `current` is not `None`), adjust the `previous.next` to skip `current`, effectively removing it.
5) If the target index is beyond the last node, do nothing.
6) Return the head of the list, which might be unchanged or updated depending on the index.
```

**⚠️ Common Mistakes**

- Incorrectly adjusting pointers, especially when removing the head or a middle node, which could lead to memory leaks or lost nodes.
- Not handling the case where `i` is exactly at the last node or beyond, which should result in no action if `i` exceeds the list length.

## I-mplement

```python
def ll_pop(head, i):
    # Check if the provided index is negative or if the list is empty
    if i < 0 or head is None:
        return head
    
    # If the node to be removed is the head
    if i == 0:
        return head.next
    
    # Initialize the pointers
    current = head
    previous = None
    count = 0
    
    # Traverse the list to find the node right before the one to be removed
    while current is not None and count < i:
        previous = current
        current = current.next
        count += 1
    
    # If we reach the index and can remove the node
    if current is not None and previous is not None:
        previous.next = current.next
    
    # Return the head of the modified list
    return head
```