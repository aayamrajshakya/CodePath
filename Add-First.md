*[[Unit 5 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What does the function return if `new_node` is added to an empty linked list?
  - The function should return the `new_node` as it becomes the head of the linked list, even if the list was previously empty.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Modify the linked list by inserting a new node at the beginning and updating the head of the list to this new node.

```markdown
1) Set the `next` attribute of the `new_node` to the current `head` of the linked list.
2) Return `new_node`, as it is now the new head of the list.
```

**⚠️ Common Mistakes**

- Returning the old `head` instead of the `new_node`.
- Not handling the `next` attribute correctly, which could lead to losing the rest of the list.

## I-mplement

```python
def add_first(head, new_node):
  new_node.next = head
  return new_node 
```