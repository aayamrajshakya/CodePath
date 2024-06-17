*[[Unit 2 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Loop through each product, and add it to a new dictionary with "pass" or "fail" depending on its score.

```markdown
1) Categorized products dict start empty
2) For each product, check score
  a) If below threshold, add product to categorized and map to "fail"
  b) Otherwise, add product to categorized and map to "pass"
3) Return the categorized products
```

## I-mplement

```python
def quality_control(product_scores, threshold):
    categorized_products = {}  # Initialize an empty dictionary
    for product_id in product_scores
        if product_scores[product_id] >= threshold:
            categorized_products[product_id] = "pass"
        else:
            categorized_products[product_id] = "fail"
    return categorized_products
``` 