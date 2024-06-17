*[[Unit 5 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What steps are necessary to create an instance of a class and use its methods?
  - First, create an instance by providing the required attributes. 
  - Second, use the class methods by calling them on the instance.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Instantiate an object of the class `Pokemon` and then call a method on this instance to perform an action.

```markdown
1) Create an instance named `squirtle` with name "Squirtle" and types ["Water"] using the Pokemon class constructor.
2) Call the `print_pokemon()` method on the `squirtle` instance to display the properties of the Pokemon.
```

**⚠️ Common Mistakes**

- Incorrect instantiation of the object without passing all required parameters to the constructor.
- Forgetting to call the method on the object.

## I-mplement

```python
squirtle = Pokemon("Squirtle", ["Water"])
squirtle.print_pokemon()
```