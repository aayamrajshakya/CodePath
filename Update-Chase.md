*[[Unit 5 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- How do we manage changes in a linked list by adding and removing nodes?
  - To remove a node, redirect any references that point to it so they no longer do. To add a node, update the `next` attribute of what should now be the last node to point to the new node.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Disconnect `dog` from the list and add a new node `cheese` at the end of the list after `mouse`.

```markdown
1) Disconnect the `dog` node from the list by setting its `next` attribute to `None`.
2) Create a node `cheese` with the value "Gouda".
3) Set the `next` attribute of the `mouse` node to point to `cheese`, adding it to the end of the list.
4) The final list structure becomes `cat -> mouse -> cheese`.
```

**⚠️ Common Mistakes**

- Incorrectly managing the `next` pointers can lead to either lost nodes or a list that does not include all intended nodes.
Failing to set `dog.next` to `None` could leave a hanging reference, potentially causing issues in list operations.

## I-mplement

```python

# Existing code
cat = Node("Tom")
mouse = Node("Jerry")
cat.next = mouse

dog = Node("Spike")
dog.next = cat

# New code
dog.next = None # notice that the node is not deleted, but is no longer connected the rest of the list

cheese = Node("Gouda")
mouse.next = cheese
```