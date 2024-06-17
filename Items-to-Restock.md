*[[Unit 2 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What if the products list is empty?
  - In this case, return an empty list.
- What if no products need to be restocked?
  - In this case you would also return an empty list.
- What should my code do if an item quantity is exactly equal to the restock threshold?
  - In this case, consider the item stocked and do not include it in your output.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Loop through each product, and make a list of any products with quantity below the threshold.

```markdown
1) If products is empty, return an empty list
2) Restock list starts empty
3) For each product and quantity:
  a) If quantity < threshold, add to restock list
4) Return restock list
```

## I-mplement

```python
def get_items_to_restock(products, restock_threshold):
    if not products:
	return []
	
    restock_list = []
    for product, quantity in products.items():
        if quantity < restock_threshold:
            restock_list.append(product)

    return restock_list
``` 