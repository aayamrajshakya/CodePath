*[[Unit 2 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What are my assumptions for this problem?
  - You may assume that each input would have exactly one solution and you may not use the same element twice. 
- Does the order the indices are returned in matter?
  - No, any order is allowed.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Using a dict, keep track of numbers we've seen so far and their indices.  For each number, check if another number exists that sums to target.  If so, return their indices.

```markdown
1) Create an empty dict to store value:index pairs
2) For each num in the list
  a) Find the needed value to make the target sum (target - num)
  b) Check if the needed value is already in our dict
    i) If yes, return the current index, and the index of the dict value
   ii) If not, add the current value:index to the dict
3) Return None if we didn't find anything
```

## I-mplement

```python
def two_sum(nums, target):
    prev_map = {}  # Value to index mapping
    
    for i in range(len(nums)):
        diff = target - nums[i]
        if diff in prev_map:
            return [prev_map[diff], i]
        prev_map[nums[i]] = i
```

*Tip: This function might seem like it's missing a `return None` line at the end.  But in Python, if you don't explicitly return anything, it automatically returns `None`.  Try it!*