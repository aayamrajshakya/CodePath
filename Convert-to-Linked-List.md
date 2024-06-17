*[[Unit 5 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- How are elements added to a linked list?
  - Each node in a linked list points to the next node through a reference called `next`.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Create two nodes representing the values "Jigglypuff" and "Wigglytuff" and link them together to form a simple linked list.

```markdown
1) Instantiate a node with the value "Jigglypuff" and store it in `jigglypuff`.
2) Instantiate another node with the value "Wigglytuff" and store it in `wigglytuff`.
3) Set the `next` attribute of `jigglypuff` to point to `wigglytuff`, creating a link between them.
```

**⚠️ Common Mistakes**

- Forgetting to link the nodes by not setting the `next` attribute.
- Misunderstanding the sequence of the list and linking nodes in the wrong orde

## I-mplement

```python
jigglypuff = Node("Jigglypuff")
wigglytuff = Node("Wigglytuff")
jigglypuff.next = wigglytuff
```