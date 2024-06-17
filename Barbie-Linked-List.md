*[[Unit 5 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What is the correct order for linking the nodes based on the given list?
  - The nodes should be linked in the order they appear: `Barbie -> President Barbie -> Weird Barbie -> Ken`.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Initialize each named node and link them together to represent the sequence given in the array.

```markdown
1) Create nodes for each character in the given order using the `Node` class.
2) Set the `next` attribute of each node to point to the subsequent node, forming a chain from the first to the last.
```

**⚠️ Common Mistakes**

- Linking nodes in the wrong order, which would misrepresent the sequence given.
- Forgetting to initialize one of the nodes, which would break the continuity of the list.

## I-mplement

```python
og_barbie = Node("Barbie")
president_barbie = Node("President Barbie")
weird_barbie = Node("Weird Barbie")
ken = Node("Ken")

og_barbie.next = president_barbie
president_barbie.next = weird_barbie
weird_barbie.next = ken
```