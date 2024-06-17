*[[Unit 2 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Does the order I add the dicts matter?
  - Yes, because if there is a duplicate element, the second catalog gets priority.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Loop through each item in catalog 2, and add/overwrite the entry in catalog 1.

```markdown
1) For each product and price in catalog 2:
  a) Set that product -> that price in catalog 1
2) Return the updated catalog 1
```

## I-mplement

```python
def merge_catalogs(catalog1, catalog2):
    for product, price in catalog2.items():
        catalog1[product] = price
    return catalog1
``` 