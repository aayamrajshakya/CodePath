*[[Unit 4 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What should the function do with an empty list?
  - It should return an empty list as reversing an empty list is still empty.
- What about lists with a single element?
  - The list should return unchanged as reversing it has no effect.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use two pointers to swap items from the start and end of the list moving towards the center.

```markdown
1) Initialize two pointers: one at the beginning (`left`) and one at the end (`right`).
2) While `left` is less than `right`:
  a) Swap the elements at `left` and `right`.
  b) Move `left` pointer one step right (increase by 1).
  c) Move `right` pointer one step left (decrease by 1).
3) Return the list as the elements are now reversed in place.
```

**⚠️ Common Mistakes**

- Not handling the case of an empty or single-element list correctly.
- Incorrectly moving the pointers or failing to swap correctly, which can result in an incorrect list or infinite loop.

## I-mplement

```python
def reverse_list(lst):
    left = 0
    right = len(lst) - 1
    
    while left < right:
        # Swap elements using a temporary variable
        temp = lst[left]
        lst[left] = lst[right]
        lst[right] = temp
        
        # Move the pointers towards the center
        left += 1
        right -= 1
    
    return lst
```