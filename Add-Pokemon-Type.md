_[[Unit 5 Session 1]] (Click for link to problem statements)_

## U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Will the method handle any checks for existing types or duplicates?
  - No, the method will simply add the new type to the list without checking for duplicates.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Implement a method `add_type()` that takes a type as a parameter and adds it to the Pokemon's type list.

```markdown
1. Define a method `add_type` that accepts a single parameter `new_type`.
2. Append `new_type` to the `types` list of the Pokemon instance.
```

**⚠️ Common Mistakes**

- Forgetting to handle the type of the parameter being added to ensure it's a string.

## I-mplement

```python

class Pokemon():
    def  __init__(self, name, types):
    self.name = name
    self.types = types
    self.is_caught = False

    def print_pokemon(self):
        print( {
            "name": self.name,
            "types": self.types,
            "is_caught": self.is_caught
        })

    def catch(self):
    self.is_caught = True

    def choose(self):
    if self.is_caught:
            print(f"{self.name} I choose you!")
    else:
        print(f"{self.name} is wild! Catch them if you can!")

    # New Code
    def add_type(self, new_type):
        self.types.append(new_type)
```
