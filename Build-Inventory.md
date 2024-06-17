*[[Unit 2 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What if `product_names` and `product_prices` are both empty?
  - In this case, return an empty dict.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Create a new dictionary using two provided lists for the keys and values

```markdown
1) Create an empty inventory dict
2) For each index in the input lists
  a) Get the name and price at current index
  b) Map name -> price in the inventory dict
3) Return the inventory dict
```

**⚠️ Common Mistakes**

- If you loop through elements in one list, it becomes tricky to find the matching element in the other list.  How can you loop through indices instead?

## I-mplement

```python
def build_inventory(product_names, product_prices):
    inventory = {}
    for i in range(len(product_names)):
        name = product_names[i]
        price = product_prices[i]
        inventory[name] = price
    return inventory
``` 