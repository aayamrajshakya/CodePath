*[[Unit 5 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What happens if the linked list has only one node?
  - The function should update the head to `None`, effectively making the list empty since the tail (which is also the head) is being removed.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Traverse the linked list to find and remove the last node (tail), updating the second-to-last node's `next` to `None`.

```markdown
1) Check if the list is empty or has only one node by examining `head` and `head.next`.
2) If the list has only one node or is empty, set `head` to `None` to represent an empty list.
3) Otherwise, traverse the list to find the second-to-last node using two pointers: `previous` and `current`.
4) Once the last node is found (`current.next` is `None`), set `previous.next` to `None` to remove the tail.
5) There's no need to return a value as the function modifies the list in place.
```

**⚠️ Common Mistakes**

- Not handling cases where the list is empty or has a single node, which requires different handling than removing nodes from longer lists.
- Incorrectly maintaining the `previous` and `current` pointers could lead to incorrect or failed removals.

## I-mplement

```python
def delete_tail(head):
    # If the list is empty or has only one node
    if head is None or head.next is None:
        return None  # After removing the tail, the list is empty
    
    # Start with the first node
    previous = None
    current = head
    
    # Traverse the list until the last node
    while current.next is not None:
        previous = current
        current = current.next
    
    # Set the second-to-last node's next to None, removing the last node
    previous.next = None
```