*[[Unit 5 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- How do we use the provided class to create an instance?
  - By using the constructor method `__init__` that has been predefined in the class to initialize a new object with specific attributes.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Instantiate a Pokemon object with the specified name and types by calling the constructor.

```markdown
1) Instantiate a Pokemon object using the class constructor, providing "Pikachu" for the name and ["Electric"] for the types.
2) Store the new object in a variable named `my_pokemon`.
```

**⚠️ Common Mistakes**

- Not using the correct syntax for object instantiation.
- Misspelling variable names or class names.

## I-mplement

```python
my_pokemon = Pokemon("Pikachu", ["Electric"])
```