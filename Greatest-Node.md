*[[Unit 5 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- How should the function behave if the linked list is empty?
  - If the list is empty (`head` is `None`), the function should return `None` as there are no values to compare.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Traverse the linked list, comparing each node's value to the current maximum, updating the maximum value as needed.

```markdown
1) If the list is empty (`head` is `None`), return `None`.
2) Initialize `max_val` with the value of the head node, assuming the list is non-empty.
3) Traverse the linked list starting from the head:
   - Compare the value of each node with `max_val`.
   - If a node's value is greater than `max_val`, update `max_val` to this new higher value.
4) After traversing all nodes, return `max_val` as the maximum value found.
```

**⚠️ Common Mistakes**

- Forgetting to handle the empty list scenario, which would lead to errors when trying to access `head.value`.
- Not properly initializing `max_val`, potentially leading to incorrect results if not set to the head's value initially.

## I-mplement

```python
    def find_max(head):
        if not head:
            return None
        
        current = head
        max_val = head.value
        while current:
            if current.value > max_val:
                max_val = current.value
            current = current.next
        
        return max_val
```