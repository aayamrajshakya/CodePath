*[[Unit 5 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What should the function return if the input `n` is zero?
  - The function should return an empty list since no nodes are requested to be listed.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Traverse the linked list starting from the head, collecting the values of the first `n` nodes into a list, or all nodes if `n` exceeds the list's length.

```markdown
1) Initialize an empty list `values` to store node values.
2) Start traversing the list from `head` with a counter initialized at 0.
3) Loop through the nodes, appending each node's value to `values` until either the end of the list is reached or `n` nodes have been processed.
4) Return the `values` list.
```

**⚠️ Common Mistakes**

- Not handling the case where `n` is greater than the number of nodes in the list, which should return all node values.
- Incorrectly setting loop conditions, leading to either excess or insufficient iterations.

## I-mplement

```python
def listify_first_n(head, n):
    # List to store the values of nodes
    values = []
    # Start from the head node
    current = head
    # Counter to track the number of nodes processed
    count = 0
    # Loop until 'current' is not None and 'count' is less than 'n'
    while current is not None and count < n:
        # Append current node's value to the list
        values.append(current.value)
        # Move to the next node
        current = current.next
        # Increment the counter
        count += 1
    # Return the list of collected values
    return values
```