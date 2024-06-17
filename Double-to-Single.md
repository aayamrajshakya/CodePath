*[[Unit 5 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- How should the new singly linked list handle the existing backward links (`prev`) from the doubly linked list?
  - The new singly linked list will ignore the `prev` links entirely, focusing only on the `next` links to recreate the list.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Convert a doubly linked list into a singly linked list by copying the values from the doubly linked list nodes into new singly linked list nodes, ignoring the `prev` links.

```markdown
1) Initialize a mock head node for the new singly linked list to facilitate easy node addition.
2) Traverse the doubly linked list starting from its head.
3) For each node in the doubly linked list:
   - Create a new node for the singly linked list with the same value.
   - Link this new node to the end of the newly forming singly linked list.
   - Advance the pointers for both the doubly linked list and the newly forming singly linked list.
4) Once all nodes are processed, return the node following the mock head as the head of the new singly linked list.
```

**⚠️ Common Mistakes**

- Neglecting to start the singly linked list with a mock head might complicate the linking process and handling of the real head of the list.
- Forgetting to move the pointer of the new singly linked list forward after appending a new node could result in an incorrect or incomplete list.

## I-mplement

```python
def dll_to_sll(dll_head):
    # Mock node to start the singly linked list
    mock_head = SLLNode(None)
    current_sll = mock_head
    
    # Current pointer for the doubly linked list
    current_dll = dll_head
    
    # Traverse the doubly linked list
    while current_dll:
        # Create a new singly linked list node with the value from DLL node
        new_node = SLLNode(current_dll.value)
        # Append it to the end of the singly linked list
        current_sll.next = new_node
        # Move the singly linked list pointer forward
        current_sll = current_sll.next
        # Move to the next node in the doubly linked list
        current_dll = current_dll.next
    
    # The head of the new singly linked list
    return mock_head.next
```