*[[Unit 2 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Will `nums` ever be empty?
  - Possibly!  In that case, there are no valid duplicates, so your program should return False.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use a dictionary to keep track of the most recent index for each element.  When we find an element for a 2nd time, we can check if its current index is within k of its most recent index.

```markdown
1) Create an empty dictionary to track recent indices
2) For each index in nums
  a) If the value is already in recent dict, compare indices
     i) If the index - recent index <= k, 
        we found a valid duplicate and can return True
  b) Update the dict with the current index
3) If we didn't find anything, return False
```

## I-mplement

```python
def hasDuplicates(nums, k):
    recent_index = {}
    for i in range(len(nums)):
        if nums[i] in recent_index:
            diff = i - recent_index[nums[i]]
            if diff <= k:
                return True
        recent_index[val] = i
    return False
```