*[[Unit 2 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- If the restock list is empty, should I return the unchanged inventory?
  - Yes.
- If the inventory is empty, what should happen?
  - All restock items would be added to the inventory.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Go through each item in the restock dictionary, and add/update it's quantity in the current inventory.

```markdown
1) Loop through each entry in the restock dictionary
  a) If the item (key) is already in the inventory, add the new quantity
  b) If this is a new item, add it to the inventory and set the new quantity
2) Return the inventory once all changes have been made 
```

**⚠️ Common Mistakes**

- Make sure you are *adding* the restock amounts to the current inventory, not *replacing* the previous amounts!

## I-mplement

```python
def restock_inventory(current_inventory, restock_list):

    # Loop over restock_list items to update current_inventory
    for item, quantity in restock_list.items():
        if item in current_inventory:
            current_inventory[item] += quantity
        else:
            current_inventory[item] = quantity
    
    return current_inventory
``` 