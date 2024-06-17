*[[Unit 4 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- How should the function behave with an empty list?
  - It should return 0 because there are no elements to process.
- Are there any constraints on the sorting of the list?
  - The list is assumed to be sorted, which allows for efficient duplicate removal.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:**  Use a two-pointer technique to modify the list in place, maintaining the order and uniqueness of elements.

```markdown
1) If the list is empty, return 0.
2) Initialize a pointer j to 1.
3) Iterate through the list from the second element:
  a) If the current element is different from the previous one, place it at the j-th position.
  b) Increment j.
4) Return j as the new length of the list.
```

**⚠️ Common Mistakes**

- Not handling the case of an empty list properly.
- Incorrectly moving the j pointer could lead to either missing unique elements or not removing all duplicates.

## I-mplement

```python
def remove_duplicates(nums):
    if not nums:
        return 0
    
    # Pointer j for the position of the next unique element
    j = 1
    
    # Iterate through the array with i
    for i in range(1, len(nums)):
        if nums[i] != nums[i-1]:
            nums[j] = nums[i]
            j += 1
            
    return j  # The new length after removing duplicates
```