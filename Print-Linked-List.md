*[[Unit 5 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- How should the function handle an empty linked list (when `head` is `None`)?
  - The function should return an empty list if no nodes are present.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Traverse the linked list starting from the head node, collect the values of each node, and return them in a list.

```markdown
1) Initialize `current` as the starting node (`head`) of the linked list.
2) Create an empty list `values` to store the values of each node encountered.
3) Traverse through the linked list:
  a) Append the value of `current` to the `values` list.
  b) Move to the next node by updating `current` to `current.next`.
4) Continue the traversal until `current` is `None`.
5) Return the list `values` containing the values of all nodes in the linked list.
```

**⚠️ Common Mistakes**

- Failing to check if the head is `None`, which could lead to attempts to access attributes of `None`.
- Not updating `current` properly, leading to an infinite loop or missing nodes.

## I-mplement

```python
class Node:
    def __init__(self, value, next=None):
        self.value = value
        self.next = next
        
def print_linked_list(head):
    current = head
    values = []
    while current:
        values.append(current.value)
        current = current.next
    return values
```