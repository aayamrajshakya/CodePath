*[[Unit 5 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What happens if an invalid item name is provided?
  - The method should not add the invalid item name to the `items` list, effectively ignoring it.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Extend the `Player` class with a method `add_item()` that checks if an item is valid before adding it to the player's `items` attribute.

```markdown
1) Define a method `add_item` that accepts an `item_name` parameter.
2) Inside the method, check if `item_name` is in the list of valid items.
3) If valid, append `item_name` to the `items` list of the player.
4) If the item is not valid, no action is taken (the method can simply exit).
```

**⚠️ Common Mistakes**

- Forgetting to check item validity before adding it to the list.

## I-mplement

```python
class Player():
    def  __init__(self, character, kart):
        self.character = character
        self.kart = kart
        self.items = []
        
    def add_item(self, item_name):
        valid_items = ["banana", "green shell", "red shell", "bob-omb", "super star", "lightning", "bullet bill"]
        if item_name in valid_items:
            self.items.append(item_name)
      
```