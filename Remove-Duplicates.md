*[[Unit 3 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Will the input list ever be empty?
  - Yes it can be, so we will want to account for this case.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Loop through the list and remove any duplicates found in the process.

```markdown
1) Check if the input list is empty, and return an empty list if so.
2) Otherwise, set an index tracker to 0
3) So long as the index tracker is smaller than the last index of the list
  a) If the integer at the current index and next index are equal, remove the current integer
  b) Otherwise, increase the index by 1
4) Return the updated list
```

## I-mplement

```python
def remove_duplicates(nums):
    if not nums:
        return []
    i = 0
    while i < len(nums)-1:
        if nums[i] == nums[i+1]:
            nums.pop(i)
        else:
            i += 1
    return nums
```