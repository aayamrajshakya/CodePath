*[[Unit 5 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What needs to be updated in the provided list to convert it into a doubly linked list?
  - Each node needs to have its `prev` attribute set to correctly point to the previous node in the list, enabling bidirectional traversal.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Properly link each node's `prev` attribute to transform the provided singly linked list into a doubly linked list.

```markdown
1) Ensure the `Node` class supports both `next` and `prev` attributes.
2) Set the `prev` attribute for each node except the head:
   - `formation.prev` should point to `crazy_in_love`.
   - `texas_hold_em.prev` should point to `formation`.
3) There is no need to set a `prev` for `crazy_in_love` as it is the first node.
```

**⚠️ Common Mistakes**

- Failing to link one of the nodes, leaving the list incorrectly structured for backward traversal.
- Incorrectly setting the `prev` links, which could lead to incorrect navigation or loops within the doubly linked list.

## I-mplement

```python
# Provided code
crazy_in_love = Node("Crazy in Love")
formation = Node("Formation")
texas_hold_em = Node("Texas Hold 'Em")
crazy_in_love.next = formation
formation.next = texas_hold_em

# Solution code
texas_hold_em.prev = formation
formation.prev = crazy_in_love
```