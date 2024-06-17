*[[Unit 5 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- How do we insert a node at the beginning of an existing linked list?
  - Create a new node and update its `next` attribute to point to the previous first node of the list.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Insert a new node `dog` at the start of the existing linked list by making it point to the `cat` node, thus updating the start of the list to `dog`.

```markdown
1) Create a node `dog` with the value "Spike".
2) Set the `next` attribute of `dog` to `cat`, making `dog` the new first node in the list.
3) The list structure now becomes `dog -> cat -> mouse`.
```

**⚠️ Common Mistakes**

- Incorrectly linking the new node, which could disrupt the current list structure.
- Misordering the operations, leading to lost references and broken links.

## I-mplement

```python
# Existing code
cat = Node("Tom")
mouse = Node("Jerry")
cat.next = mouse

# New code
dog = Node("Spike")
dog.next = cat
```