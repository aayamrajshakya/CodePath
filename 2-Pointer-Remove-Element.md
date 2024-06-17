*[[Unit 4 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What happens to the elements in the array after the specified value is removed?
  - They should be moved to the front of the array in their original order, and the remaining space will not be considered.
- Are there constraints on modifying the array?
  - The operation must be done in-place, and no extra space for another array should be used.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Iterate through the array with a fast pointer to examine each element. Use a slow pointer to place elements that are not equal to the target value.

```markdown
1) Initialize a slow pointer `i` at the start of the array.
2) For each element in the array (`j` as the fast pointer):
  a) If the element at `j` is not equal to `val`:
     i) Place the element at the slow pointer's current position.
    ii) Increment the slow pointer `i`.
3) Return the position of the slow pointer, which indicates the new length of the array.
```

**⚠️ Common Mistakes**

- Mismanaging the pointers which can lead to missing elements or incorrect placements.
- Returning the whole list instead of the new length of the relevant part of the list.

## I-mplement

```python
def removeElement(nums, val):
    i = 0  # Start from the first element
    for j in range(len(nums)):
        if nums[j] != val:
            nums[i] = nums[j]
            i += 1
    return i
```