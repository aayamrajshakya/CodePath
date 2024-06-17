*[[Unit 2 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Will the original dict be modified?
  - Yes.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** First, make a list of keys to remove.  Next, actually remove them and add them to a results list.

```markdown
1) Create an empty list to store keys to remove
2) Loop through the keys of the items dict
  a) If the price for that key is below threshold, add to list
3) If the list of items to remove is empty, return None
4) Loop through the list of items to remove
  a) For each item, remove the dictionary entry for that key
5) Return the list of items to remove
```

**⚠️ Common Mistakes**

- If you remove things from a dict WHILE looping through the dict, your program will likely not work as intended.

## I-mplement

```python
def remove_items_below_price(items, price_threshold):
    # Initialize a list to hold the names of items that will be removed
    items_to_remove = []

    # Collect item names to remove in a separate list to avoid modifying the dictionary while iterating
    for item, price in items.items():
        if price < price_threshold:
            items_to_remove.append(item)

    # Check if any item meets the condition; if not, return None
    if not items_to_remove:
        return None

    # Remove the items from the dictionary and prepare a list of removed items
    removed_items = []
    for item in items_to_remove:
        removed_items.append(item)
        items.pop(item)

    return removed_items
```