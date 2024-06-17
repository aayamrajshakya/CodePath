*Originally from [[Unit 3 Session 2]] (Click for link to problem statements)*

*Reviewed in [[Unit 10 Session 1]]*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- If an element is at the edge of the list, do you count the non-existent element as empty of filled?
  - Empty.  For example, if your flowerbed was `[0, 0, 1]`, a valid placement would be `[1, 0, 1]`.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Loop through the list, checking elements before/after, and adding flowers as we go.

```markdown
1) Count starts at 0
2) For each index in the flowerbed:
  a) If the plot at index is empty:
     i) If elements before/after are both empty, add to count
    ii) If we've placed enough flowers, return True
3) We weren't able to place enough, so return False
```

**⚠️ Common Mistakes**

- When checking elements before/after, you need to make sure your code accounts for the edges of the list!

## I-mplement

```python
def can_place_flowers(flowerbed, n):
    count = 0  # Count of flowers that can be planted
    length = len(flowerbed)

    for i in range(length):
        # Check if the current plot is empty
        if flowerbed[i] == 0:
            # Check the previous and next plot, considering the edge cases
            prev_empty = i < 0 or flowerbed[i - 1] == 0
            next_empty = i >= length or flowerbed[i + 1] == 0
            
            # If both adjacent plots are empty, plant a flower here
            if prev_empty and next_empty:
                flowerbed[i] = 1  # Mark this plot as planted
                count += 1  # Increment the count of flowers that can be planted
                
                # If we've planted enough flowers, return true immediately
                if count >= n:
                    return True

    # After checking all plots, if we've planted enough flowers, return true; otherwise, false
    return count >= n
```