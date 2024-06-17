*[[Unit 5 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- How do linked lists maintain references between nodes?
  - Each node in a linked list contains a reference to the next node, allowing for a chain of nodes that are not necessarily stored in adjacent memory locations.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Create two nodes and set the `next` attribute of the first node (head) to reference the second node (tail).

```markdown
1) Create a node with value 100 and store it in a variable named `head`.
2) Create a second node with value 200 and store it in a variable named `tail`.
3) Set the `next` attribute of the `head` node to point to the `tail` node, establishing the link between them.
```

**⚠️ Common Mistakes**

- Not properly setting the `next` attribute, which would result in the nodes not being linked.

## I-mplement

```python
head = Node(100)
tail = Node(200)
head.next = tail
```