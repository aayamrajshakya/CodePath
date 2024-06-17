*[[Unit 5 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What should be done if the head node is `None`?
  - If the head node is `None`, indicating an empty linked list, the function should print nothing or state that the list is empty.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Traverse the linked list starting from the head node, collect the values of each node, and print them connected by " -> ".

```markdown
1) Start with the head node of the linked list.
2) Traverse the list by moving from one node to its `next` node.
3) Collect each node's value in a list called `values`.
4) After traversing all nodes, join the values in `values` with " -> " and print the result.

```

**⚠️ Common Mistakes**

- Forgetting to handle the case where the linked list is empty.
- Incorrect handling of the `next` pointer, potentially causing an infinite loop if not moved correctly.

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
    print(" -> ".join(values))
```