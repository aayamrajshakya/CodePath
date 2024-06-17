*[[Unit 5 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- How can the function find the length of the list starting from any node?
  - One strategy would be to find the beginning of the list first.  Because this is a doubly-linked list, it's actually fairly simple to do!

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Calculate the total number of nodes in a doubly linked list from a given node by first finding the head of the list and then counting each node until reaching the end.

```markdown
1) Check if the given node is `None`; return 0 if true.
2) Move backwards through the list from the given node to find the head of the list.
3) Starting from the head, count all nodes in the list until the end is reached.
4) Return the count as the length of the list.
```

**⚠️ Common Mistakes**

- Incorrectly handling the start of traversal, potentially missing the actual start of the list.
- Not correctly counting the nodes, either by starting the count incorrectly or by stopping the count prematurely.

## I-mplement

```python
def get_length(node):
    if node is None:
        return 0

    # Find the start of the list
    start = node
    while start.prev:
        start = start.prev

    # Traverse from start to end, counting nodes
    length = 0
    current = start
    while current:
        length += 1
        current = current.next

    return length
```