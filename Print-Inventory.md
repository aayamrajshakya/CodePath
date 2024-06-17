*[[Unit 5 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- How should the method handle multiple instances of the same item?
  - It should count and display each item type along with its quantity.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Implement a method `print_inventory()` in the Player class that summarizes the player's items and their quantities, or indicates an empty inventory.

```markdown
1) Define a method `print_inventory` within the Player class.
2) Check if the player’s `items` list is empty.
   - If yes, print "Inventory empty."
   - If no, count each type of item in the list.
3) Prepare a string to display the inventory items along with their counts.
4) Iterate through the item counts and format them into the display string.
5) Print the formatted inventory list.
```

**⚠️ Common Mistakes**

- Failing to initialize or update the item count correctly.
- Incorrectly formatting the output string, which could lead to a misleading or unclear display.

## I-mplement

```python
class Player:
    def __init__(self, character, kart):
        self.character = character
        self.kart = kart
        self.items = []

    def add_item(self, item_name):
        valid_items = ["banana", "green shell", "red shell", "bob-omb", "super star", "lightning", "bullet bill"]
        if item_name in valid_items:
            self.items.append(item_name)
            
    # New code:       
    def print_inventory(self):
        if not self.items:
            print("Inventory empty.")
        else:
            item_count = {}
            for item in self.items:
                if item in item_count:
                    item_count[item] += 1
                else:
                    item_count[item] = 1

            inventory_display = ""
            first = True
            for item, count in item_count.items():
                if not first:
                    inventory_display += ", "
                inventory_display += f"{item}: {count}"
                first = False

            print(f"Inventory: {inventory_display}")
	  
```
