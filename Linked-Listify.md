*[[Unit 5 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- How should the function handle an empty list?
  - If the input list `lst` is empty, the function should return `None` since there would be no nodes to create.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Convert an array of values into a linked list, starting with the first value as the head and linking subsequent values.

```markdown
1) Check if the input list `lst` is empty and return `None` if true.
2) Create the head of the linked list with the first element of `lst`.
3) Traverse the remaining elements of `lst`, creating a new node for each and linking it to the list.
4) Return the head of the newly formed linked list.
```

**⚠️ Common Mistakes**

- Forgetting to handle the case of an empty input list, which should return `None`.
- Errors in linking nodes could lead to incorrect or incomplete linked list structure.

## I-mplement

```python
def list_to_linked_list(lst):
    if not lst:  # Check if the array is empty
        return None
    head = Node(lst[0])  # Create the head node with the first element
    current = head
    for value in lst[1:]:  # Iterate over the rest of the elements
        current.next = Node(value)  # Create a new node and link it
        current = current.next
    return head
```