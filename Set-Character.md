*[[Unit 5 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- How does the class method validate the character name before updating?
  - The method checks if the provided name is within a list of valid character names.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Implement a setter method `set_character()` within the `Player` class that updates the character attribute after validating the input against a list of allowed characters.

```markdown
1) Define a method `set_character` with a parameter `name`.
2) Check if the `name` is within the predefined list of valid characters.
3) If valid, update the `character` attribute and print "Character updated".
4) If not valid, print "Invalid character".
```

**⚠️ Common Mistakes**

- Not including all valid characters in the list, which could falsely invalidate a correct input.
- Misnaming the method or the parameter, potentially leading to syntax or logical errors.

## I-mplement

```python
class Player():
    def  __init__(self, character, kart):
        self.character = character
        self.kart = kart
        self.items = []
        
    def set_player(self, name):
        valid_characters = ["Mario", "Luigi", "Peach", "Yoshi", "Toad", "Wario", "Donkey Kong", "Bowser"]
        if name in valid_characters:
            self.character = name
            print("Character updated")
        else:
            print("Invalid character")
```