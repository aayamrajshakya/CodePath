*[[Unit 5 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What happens when the `choose()` method is called on a Pokemon that is not caught?
  - The method should indicate that the Pokemon is still wild.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Add a method `choose()` to the Pokemon class that checks the caught status and prints a message based on whether the Pokemon is caught or not.

```markdown
1) Add a method `choose` to the class.
2) In `choose`, check if the Pokemon `is_caught`.
3) If caught, print "<Pokemon name> I choose you!".
4) If not caught, print "<Pokemon name> is wild! Catch them if you can!".
```

**⚠️ Common Mistakes**

- Forgetting to use the f-string for dynamic text output in Python.
- Misunderstanding the condition for checking `is_caught` status.

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
      
```