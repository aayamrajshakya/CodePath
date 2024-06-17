*[[Unit 5 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What should occur if there is only one node in the linked list when the function is called?
  - The new node should become the second node in the list, and the existing node (head) should link to it directly.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Add a new node immediately after the head of the linked list, updating the links to incorporate the new node as the second node in the list.

```markdown
1) Create a new node with the specified value `val`.
2) Link the new node to the current second node in the list (`head.next`).
3) Set `head.next` to point to the new node, inserting it as the second node.
4) Return the original head of the list, which remains the first node.
```

**⚠️ Common Mistakes**

- Incorrectly linking the new node which could either bypass the original second node or disrupt the list.
- Returning the new node instead of the original head, which would misrepresent the start of the list.

## I-mplement

```python
def add_second(head, val):
    # Create the new node that needs to be added
    new_node = Node(val)
    
    # Insert the new node as the second node
    new_node.next = head.next
    head.next = new_node
    
    # Return the unchanged head of the list
    return head
```