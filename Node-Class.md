*[[Unit 5 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- How do we ensure that each node is initialized correctly?
  - Each node must be instantiated with its respective value, confirming that the constructor correctly sets up the node with this value.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Utilize the provided Node class to create two separate nodes, each initialized with specific values, and store them in designated variables.

```markdown
1) Instantiate a node with the value 'a' and store it in the variable `node_one`.
2) Instantiate another node with the value 'b' and store it in the variable `node_two`.
```

**⚠️ Common Mistakes**

- Incorrectly setting the value of a node.
- Not using the correct syntax for creating an instance of a class.

## I-mplement

```python
node_one = Node('a')
node_two = Node('b')
```