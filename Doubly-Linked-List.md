*[[Unit 5 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What should be the relationship between each `Node` in a doubly linked list?
  - Each node should point to both the next and the previous nodes in the list, facilitating bidirectional traversal.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Construct a doubly linked list from the given array of values, ensuring each node is correctly linked in both directions.

```markdown
1) Create nodes for "Poliwag", "Poliwhirl", and "Poliwrath".
2) Set the `next` attribute of each node to link to the subsequent node.
3) Set the `prev` attribute of each node to link to the previous node.
4) Ensure that the first node's `prev` is `None` and the last node's `next` is `None`.
```

**⚠️ Common Mistakes**

- Not setting the `prev` attribute correctly, which could lead to incorrect or incomplete backward links.
- Forgetting to handle the ends of the list where `prev` or `next` should be `None`.

## I-mplement

```python
poliwag = Node("Poliwag")
poliwhirl = Node("Poliwhirl")
poliwrath = Node("Poliwrath")

poliwag.next = poliwhirl
poliwhirl.next = poliwrath

poliwrath.prev = poliwhirl
poliwhirl.prev = poliwag
```