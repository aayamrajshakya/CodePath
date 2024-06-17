*[[Unit 5 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- How do we handle finding the tail in a single-node list?
  - If the list has only one node (`head`), that node is both the head and the tail, so we return its value.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Traverse the linked list starting from the head until reaching the last node, and return its value as the tail.

```markdown
1) Check if the list is empty (`head` is `None`). If it is, return `None`.
2) Initialize a variable `current` to `head` to start traversal.
3) Use a loop to navigate through the list until reaching the last node (where `current.next` is `None`).
4) Return the value of `current` as the value of the tail node.
```

**⚠️ Common Mistakes**

- Neglecting to handle the edge case where the list is empty, which should promptly return `None`.
- Incorrectly navigating through the list or stopping the traversal prematurely.

## I-mplement

```python
def get_tail(head):
  if not head:
    return None
  current = head
  while current.next:
    current = current.next
  return current.value

```