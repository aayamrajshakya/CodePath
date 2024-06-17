*[[Unit 5 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What should happen if the list contains only one element?
  - If there is only one node in the list, the function should return the list unchanged because the head and the tail are the same.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Rearrange the nodes in the linked list by moving the last node (tail) to the position of the first node (head), and adjusting the necessary links to maintain the list's integrity.

```markdown
1) Check if the list is empty or contains only one node; return the head as is in these cases.
2) Traverse the linked list to identify the tail node and the second-to-last node.
3) Disconnect the tail from the rest of the list by setting the `next` of the second-to-last node to `None`.
4) Set the `next` of the tail to the current head, linking the tail to the front of the list.
5) Update the head to point to the tail node, now moved to the front.
6) Return the new head of the list.
```

**⚠️ Common Mistakes**

- Not properly handling edge cases where the list is either empty or has only one node.
- Failing to correctly update the `next` pointer of the second-to-last node, which could leave the list in an incorrect state.
- Incorrectly moving the pointers, resulting in the tail not being properly placed at the head or causing a loop in the list.

## I-mplement

```python
def tail_to_head(head):
    if head is None or head.next is None:
        # If the list is empty or has only one node, return as is
        return head
    
    # Initialize pointers
    second_last = None
    tail = head
    
    # Traverse to find the tail and the second-to-last node
    while tail.next:
        second_last = tail
        tail = tail.next
    
    # Move the tail to the front
    second_last.next = None  # Break the link
    tail.next = head         # Set the tail's next to the former head
    head = tail              # Update head to the new head (former tail)
    
    return head
```