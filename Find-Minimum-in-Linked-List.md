*[[Unit 5 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What should the function return if the linked list is empty?
  - If the linked list is empty (`head` is `None`), the function should return `None` to indicate there are no values to compare.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Traverse the linked list and find the minimum numeric value among the nodes.

```markdown
1) Check if the linked list is empty; return `None` if true.
2) Initialize `min_val` with the value of the head node.
3) Traverse the linked list, comparing the value of each node with `min_val`.
4) If a node's value is less than `min_val`, update `min_val`.
5) Continue until the end of the list is reached.
6) Return `min_val` as the smallest value in the list.
```

**⚠️ Common Mistakes**

- Incorrectly initializing `min_val`, which could lead to incorrect comparisons or results.
- Not handling the case where the list might be empty, which should gracefully return `None`.


## I-mplement

```python
    def find_min(head):
        if not head:
            return None
        
        current = head
        min_val = head.value
        while current:
            if current.value < max_val:
                min_val = current.value
            current = current.next
        
        return min_val
```