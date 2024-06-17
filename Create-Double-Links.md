*[[Unit 5 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- How does the constructor need to be structured to support both forward and backward traversal in a doubly linked list?
  - The constructor must initialize each node with `next` and `prev` attributes, allowing links to both the subsequent and preceding nodes.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Modify the `Node` class constructor to include both `next` and `prev` parameters, initializing them to `None` by default. This setup will allow each node to potentially link to both the next and previous nodes in a doubly linked list.

```markdown
1) Define the class `Node` with the constructor accepting `value`, `next`, and `prev` parameters.
2) Initialize the `value` attribute to hold the node's data.
3) Set the `next` attribute to point to the next node in the list, defaulting to `None`.
4) Set the `prev` attribute to reference the previous node in the list, also defaulting to `None`.
```

**⚠️ Common Mistakes**

- Omitting the initialization of the `prev` attribute, which is essential for the backward linkage in a doubly linked list.
- Failing to correctly handle default parameters, potentially leading to nodes that are not correctly linked.

## I-mplement

```python
class Node:
	def __init__(self, value, next = None, prev = None):
		self.value = value
		self.next = next
		self.prev = prev
```