*[[Unit 5 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What should the function do if the index `i` is out of the list's current bounds?
  - If `i` is beyond the current end of the list, the new node should be inserted at the end of the list.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Insert a new node at the specified index in the linked list, handling edge cases where `i` is 0 or beyond the end of the list.

```markdown
1) If the list is empty (`head` is `None`), create a new node with the value and return it as the new head.
2) If the index `i` is 0, insert the new node before the current head and return the new node as the new head.
3) Use a loop to find the correct position in the list where the new node should be inserted:
   a) Traverse the list until reaching the position just before the index `i`.
   b) Insert the new node at index `i` by adjusting the `next` pointers.
4) If `i` exceeds the length of the list, append the new node at the end.
5) Return the head of the list.
```

**⚠️ Common Mistakes**

- Failing to adjust the `next` pointers correctly, which could lead to losing part of the list.
- Not considering the case where `i` is greater than the number of nodes, which should not throw an error but append the node at the end.

## I-mplement

```python
def ll_insert(head, val, i):
    # Handle the case where the list is initially empty or `i` is 0
    if not head or i == 0:
        return Node(val, head)

    # Traverse to find the insertion point
    current = head
    count = 1  # Start count at 1 since we've already handled `i == 0`
    while current:
        # Insert at index `i` by adjusting the `next` pointers
        if count == i:
            new_node = Node(val, current.next)
            current.next = new_node
            return head
        current = current.next
        count += 1

    # If `i` was beyond the end, append to the last
    if count < i:
        current.next = Node(val)

    return head
```