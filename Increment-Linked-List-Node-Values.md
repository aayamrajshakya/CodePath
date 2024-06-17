*[[Unit 5 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Does the function need to handle any specific constraints or conditions regarding the node values or list size?
  - The function should be prepared to increment any integer values and work efficiently regardless of the list's length, assuming the list is not empty.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Traverse the linked list and increment the value of each node by 1, ensuring all nodes are updated correctly without changing the structure of the list.

```markdown
1) Start at the head of the list.
2) Traverse through the list node by node.
3) For each node encountered, increment its stored value by 1.
4) Continue until the end of the list is reached.
5) Return the head of the list, which remains unchanged except for the values being incremented.
```

**⚠️ Common Mistakes**

- Failing to traverse the entire list or incorrectly updating node values.
- Mistakenly modifying the list structure or node links during the value increment process.

## I-mplement

```python
def increment_ll(head):

  current = head
  while current:
    current.value += 1
    current = current.next
  return head
```