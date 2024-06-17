*[[Unit 5 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What should happen if the first node (head) contains the value `val`?
  - If the head node has the value `val`, it should be removed and the function should return the next node as the new head of the list.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Traverse the linked list to find and remove the first node with the given value `val`. Adjust the links appropriately to maintain the list's integrity.

```markdown
1) Check if the linked list is empty; if so, return the head as is.
2) Check if the head node contains the value `val`:
   - If it does, set the head to `head.next` to remove the first node and return the new head.
3) Use two pointers, `previous` and `current`, to traverse the list:
   - `previous` starts at the head, and `current` starts at `head.next`.
   - Loop through the list to find the node with value `val`.
   - If found, adjust `previous.next` to skip `current`, effectively removing it from the list.
4) Return the head of the list, which could be unchanged if no node with `val` was found.
```

**⚠️ Common Mistakes**

- Not properly handling the case where the node to remove is the `head`.
- Failing to update the `next` pointer of the `previous` node, which could leave the list incorrectly linked.
- Returning the head inside the loop, which could stop the function prematurely without removing the node.

## I-mplement

```python
def ll_remove(head, val):
    # Check if the list is empty
    if head is None:
        return head

    # If the node to be removed is the head of the list
    if head.value == val:
        return head.next

    # Initialize pointers
    current = head.next
    previous = head

    # Traverse the list to find the node to remove
    while current:
        if current.value == val:
            # Remove the node by skipping it
            previous.next = current.next
            return head
        previous = current
        current = current.next

    # If no node was found with the value `val`, return the original head
    return head
```