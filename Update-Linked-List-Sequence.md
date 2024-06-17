*[[Unit 5 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- How do the additions of the new nodes affect the overall structure of the linked list?
  - The new nodes `orange` and `green` are inserted between the existing nodes, extending the list while maintaining the original order for the remaining nodes.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Insert two new nodes (`orange` and `green`) into specific positions in the existing linked list to form the sequence `red -> orange -> yellow -> green -> blue`.

```markdown
1) Create two new nodes, `orange` and `green`, for insertion.
2) Adjust the `next` pointers to incorporate the new nodes into the list:
   - Set `red.next` to `orange`.
   - Set `orange.next` to `yellow`.
   - Set `yellow.next` to `green`.
   - Set `green.next` to `blue`.
3) Ensure the list now follows the order of `red`, `orange`, `yellow`, `green`, `blue`.
```

**⚠️ Common Mistakes**

- Incorrectly linking the nodes which could disrupt the sequence or leave some nodes unlinked.
- Not updating the next pointers in the correct order, which might result in losing track of some parts of the list.

## I-mplement

```python
# Existing code
red = Node('red')
yellow = Node('yellow')
blue = Node('blue')
red.next = yellow
yellow.next = blue

# New Code
orange = Node('orange')
green = Node('green')

red.next = orange
orange.next = yellow
yellow.next = green
green.next = blue
```