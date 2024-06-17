*[[Unit 2 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What if I reduce an items stock to exactly 0?
  - In that case, remove the item from the dictionary -- stock should always be 1 or higher.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Check if the operation is valid, and if so, deduct the stock and return the updated dict.

```markdown
1) If the item does not exist, return an error message
2) If the quantity requested > stock, return an error message
3) Reduce the item stock by the requested quantity
4) If the stock is reduced to zero, remove from items dict
5) Return updated items dict
```

## I-mplement

```python
def pop_stock(items, item_name, quantity):
    if item_name not in items:
        return "Item does not exist."
    if quantity > items[item_name]:
        return "Not enough stock."
    items[item_name] -= quantity
    if items[item_name] <= 0:
        items.pop(item_name)
    return items
```
