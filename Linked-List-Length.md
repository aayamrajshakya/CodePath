*[[Unit 5 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- How does the function behave if the linked list is empty (`head` is `None`)?
  - The function should return 0, indicating that there are no nodes in the list.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Traverse the linked list from the head to the end, counting each node until no more nodes are left.

```markdown
1) Initialize a counter `count` to zero to track the number of nodes.
2) Start at the `head` and traverse the list using a loop.
3) For each node encountered, increment the `count`.
4) Once the end of the list is reached (`current` becomes `None`), return the `count`.
```

**⚠️ Common Mistakes**

- Forgetting to increment the count within the loop, which could result in returning zero regardless of the list's length.
- Mishandling the end condition where the list is empty, which should still correctly return 0.

## I-mplement

```python
def ll_length(head):
  count = 0

  current = head
  while current:
    count += 1
    current = current.next
  return count
```