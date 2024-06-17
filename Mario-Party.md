*[[Unit 5 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Are there any special conditions for setting up the linked list beyond linking the nodes?
  - No special conditions, just create nodes for each element and link them sequentially.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Construct a linked list that corresponds to the order of names in the array ["Mario", "Luigi", "Wario", "Toad"].

```markdown
1) Create a node for each character: Mario, Luigi, Wario, and Toad.
2) Link each node to the next one in the list, setting the `next` attribute appropriately.
```

**⚠️ Common Mistakes**

- Not linking the nodes in the correct sequence as listed.
- Trying to incorrectly link the final node, which should not have a `next` node set (it should remain `None`).

## I-mplement

```python
head = Node('Mario')
second = Node('Luigi')
third = Node('Wario')
tail = Node('Toad')

head.next = second
second.next = third
third.next = tail
```