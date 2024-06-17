*[[Unit 5 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What does it mean to find the "first middle node" in the context of a linked list with an even number of nodes?
  - In such cases, you should return the node that appears first among the two central nodes.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Calculate the middle of the linked list by first counting the total number of nodes and then retrieving the node at the middle index during a second pass.

```markdown
1) Conduct a first pass to count all nodes in the linked list to determine its length.
2) Compute the middle index based on the total length divided by two, rounding down if necessary.
3) Perform a second pass through the list, stopping at the node that corresponds to the middle index.
4) Return the node at this index, which represents the "first middle node" in cases where there are two middle nodes.
```

**⚠️ Common Mistakes**

- Miscounting nodes or incorrectly handling the traversal could result in reaching the wrong node or even a runtime error.
- Not properly calculating the middle index or failing to consider lists with an even number of nodes.

## I-mplement

```python
def find_middle_node(head):
    # First pass: count the number of nodes in the list
    current = head
    total_count = 0
    while current:
        total_count += 1
        current = current.next
    
    # Find the middle index
    middle_index = int(total_count / 2)
    
    # Second pass: reach the middle node
    current = head
    current_index = 0
    while current_index < middle_index:
        current = current.next
        current_index += 1
    
    # Return the node at the middle index
    return current
```

Alternatively, this solution can be simplified by using the `ll_length()` method from [[Linked List Length]]:

```python
def find_middle_node(head):
    # First pass: count the number of nodes in the list
    length = ll_length(head)
    
    # Find the middle index
    middle_index = int(length / 2)
    
    # Reach the middle node
    current = head
    current_index = 0
    while current_index < middle_index:
        current = current.next
        current_index += 1
    
    # Return the node at the middle index
    return current
```
