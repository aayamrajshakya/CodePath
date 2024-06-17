*[[Unit 5 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What should the function do if the `tail` is `None` (i.e., the list is empty)?
  - If the list is empty, the function should print an empty string or handle the case gracefully without errors.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Traverse the doubly linked list starting from the tail, collect values, and print them in reverse order.

```markdown
1) Start at the `tail` node of the doubly linked list.
2) Traverse backwards using the `prev` attribute of each node to collect the values.
3) Store each value in a list.
4) Join the list of values into a string with spaces and print the result.
```

**⚠️ Common Mistakes**

- Forgetting to convert node values to strings before joining them, which could raise a TypeError if the values are not strings.
- Not handling the empty list case, leading to potential errors or incorrect outputs.

## I-mplement

```python
def print_reverse(tail):
    values = []
    current = tail
    while current:
        values.append(str(current.value))
        current = current.prev
    print(" ".join(values))
```