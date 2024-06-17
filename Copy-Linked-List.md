*[[Unit 5 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What happens if the original linked list is empty (`head` is `None`)?
  - The function should correctly handle this by returning `None`, indicating that the copied list is also empty.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Create a new linked list that is a complete copy of the original list, ensuring that no nodes from the original list are reused.

```markdown
1) Begin with a mock head node to simplify the process of adding new nodes to the new linked list.
2) Traverse the original linked list node by node.
3) For each node in the original list, create a new node with the same value and link it to the new list.
4) Continue until all nodes in the original list have been copied.
5) Return the next node after the mock head as the head of the new linked list.
```

**⚠️ Common Mistakes**

- Neglecting to handle the case where the original list might be empty, which should result in an empty new list.
- Incorrectly linking the new nodes or not properly advancing the pointers, which could lead to an incomplete copy or a list that doesn't end properly.

## I-mplement

```python
def copy_ll(head):
    # Mock node to start the new linked list
    mock_head = Node(0)
    current_new = mock_head
    
    # Current pointer for the original linked list
    current_original = head
    
    # Traverse the original linked list
    while current_original:
        # Create a new node with the same value as the original node
        new_node = Node(current_original.value)
        # Append it to the end of the new linked list
        current_new.next = new_node
        # Move the new list pointer forward
        current_new = current_new.next
        # Move to the next node in the original linked list
        current_original = current_original.next
    
    # The head of the new singly linked list
    return mock_head.next
```