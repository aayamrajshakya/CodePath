*[[Unit 5 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- How does the function handle the insertion of a new head when the original list is empty (i.e., `head` is `None`)?
  - The function will still work correctly, setting the `next` of the new node to `None`, effectively making it the head and only node in the list.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Implement a function to prepend a new node with a given value to the front of the linked list, making it the new head.

```markdown
1) Create a new node with the provided value `val`.
2) Set the `next` attribute of this new node to the current head of the list, linking it to the existing list.
3) Return the new node, which is now the head of the list.
```

**⚠️ Common Mistakes**

- Forgetting to link the new head to the existing list, which could result in losing all other nodes.
- Incorrectly handling the return value, potentially not updating the head properly.

## I-mplement

```python
def add_first(head, val):
    # Create a new Node object with the value 'val'
    new_head = Node(val)
    
    # Link the new node to the existing head of the list
    new_head.next = head
    
    # Return the new head of the list
    return new_head
```