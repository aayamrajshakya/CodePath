*[[Unit 5 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- How do we properly link two nodes in a linked list?
  - Each node has a `next` attribute, which should be set to reference the next node in the sequence.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use the `Node` class to create two nodes named `cat` and `mouse` with respective values "Tom" and "Jerry", and then link them to form a linked list.

```markdown
1) Create a node `cat` with the value "Tom".
2) Create a second node `mouse` with the value "Jerry".
3) Set the `next` attribute of `cat` to point to `mouse`, linking the two nodes.
```

**⚠️ Common Mistakes**

- Not correctly setting the next attribute, which would leave the nodes unlinked.
- Mixing up the order of node creation and linking, which could create a reference before the object exists.

## I-mplement

```python
cat = Node("Tom")
mouse = Node("Jerry")
cat.next = mouse
```