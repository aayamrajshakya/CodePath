*[[Unit 5 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What should the function do if the linked list is empty?
  - If the linked list is empty, the function should return an empty string or a specific message indicating that the list has no elements.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Traverse the linked list starting from the head, collect all node values, and then join them into a single string with "chases" as a separator.

```markdown
1) Initialize a variable `current` to `head` to start at the beginning of the list.
2) Create an empty list `values` to hold the values of each node.
3) Use a loop to traverse the linked list:
   - Append the value of `current` to the `values` list.
   - Move to the next node by updating `current` to `current.next`.
4) Join all elements in `values` with " chases " as the separator and print or return the result.
```

**⚠️ Common Mistakes**

- Not handling the case where the linked list might be empty, which could lead to an error when trying to access attributes of `None`.
- Incorrectly handling the join operation, potentially leading to syntax errors or a wrong output format.

## I-mplement

```python
class Node:
    def __init__(self, value, next=None):
        self.value = value
        self.next = next
        
def print_linked_list(head):
    current = head
    values = []
    while current:
        values.append(current.value)
        current = current.next
    print(" chases ".join(values))
```