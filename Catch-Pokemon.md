*[[Unit 5 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Do we need to modify any of the existing class methods?
  - No.  You only need to add the new method.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Extend the Pokemon class by adding a new method `catch()` which sets the `is_caught` attribute to True.

```markdown
1) Define a method `catch` within the Pokemon class that changes `is_caught` to True.
2) This method does not take parameters other than `self` and does not return any value.
```

**⚠️ Common Mistakes**

- Not including the `self` parameter in the method definition.
- Attempting to return a value from a method that should only update an attribute.

## I-mplement

```python
class Pokemon:

    def __init__(self, name, types):
        self.name = name
        self.types = types
        self.is_caught = False

    def print_pokemon(self):
        print {'name': self.name, 'types': self.types,
               'is_caught': self.is_caught}

    # New code:
    def catch(self):
        self.is_caught = True
```
