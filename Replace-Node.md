*[[Unit 5 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What happens if the `original` value is not found in any node?
  - The function will traverse the entire list without making any changes, leaving the linked list unchanged.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Traverse the linked list from the head, checking each node's value and replacing it if it matches the `original` value.

```markdown
1) Start at the `head` of the linked list.
2) Traverse through the list using a loop, checking each node's value.
3) If a node's value matches `original`, update it to `replacement`.
4) Continue until all nodes have been checked (i.e., until the end of the list).
```

**⚠️ Common Mistakes**

- Failing to handle cases where the list is empty (i.e., `head` is `None`).
- Not correctly updating the node value or missing nodes due to incorrect loop conditions.

## I-mplement

```python
def ll_replace(head, original, replacement):
  current = head
  while current:
    if current.value == original:
      current.value = replacement
    current = current.next
```