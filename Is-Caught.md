*[[Unit 5 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- How do you update an attribute of an object and verify the update?
  - Change the attribute's value directly and call a method to print the updated information.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Modify the `is_caught` attribute of the previously created `squirtle` object and then use a method to confirm the update.

```markdown
1) Set the `is_caught` attribute of `squirtle` to True to indicate that it has been caught.
2) Call the `print_pokemon()` method to print the current state of `squirtle`, verifying the attribute update.
```

**⚠️ Common Mistakes**

- Not using the correct syntax to access and modify object attributes.

## I-mplement

```python
squirtle.is_caught = True
squirtle.print_pokemon()
```