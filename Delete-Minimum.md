*[[Unit 3 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What if there are duplicate elements?
  - Duplicates can be removed in any order.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** While there is still something in the original list, find the smallest value and remove it. 

```markdown
1) Create an empty list for removal order
2) While the input list is not empty:
  a) Find the minimum element
  b) Remove it from the input list
  c) Add it to the removal list
3) Return the removal list
```

## I-mplement

```python
def delete_minimum_elements(nums):
    removed_order = []
    while nums:
        min_val = min(nums)
        nums.remove(min_val)
        removed_order.append(min_val)
    return removed_order
```