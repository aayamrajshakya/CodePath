*[[Unit 5 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- How does the insertion of a new node affect the existing structure of the linked list?
  - The new node (middle) is placed between two existing nodes (head and tail), changing the `next` references to maintain the list order.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Insert the `middle` node between `head` and `tail` by adjusting the `next` pointers to link all three nodes sequentially.

```markdown
1) Create the `middle` node with a value of 150, initially linking it directly to `tail`.
2) Adjust the `next` pointer of the `head` node to point to the new `middle` node.
3) This establishes the order: head -> middle -> tail in the linked list.
```

**⚠️ Common Mistakes**

- Incorrectly setting the `next` pointers could disrupt the linked list's structure, either by skipping a node or creating a loop.
- Not understanding the initial conditions from previous problems could lead to incorrect linking.

## I-mplement

```python
# Existing code
head = Node(100)
tail = Node(200)
head.next = tail

middle = Node(150, tail)
head.next = middle
```