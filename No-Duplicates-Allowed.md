*[[Unit 2 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Loop backwards through the list, and each time we find a new element, add it to the front of a new list.

```markdown
1) Create an empty list to store unique numbers
2) Starting at the END of the nums list:
  a) If the number is not already in unique,
     insert it at the beginning of unique
3) Return the unique nums
```

## I-mplement

```python
def remove_duplicates_from_front(nums):
    unique_nums = []
    for i in range(len(nums)-1, -1, -1):
        if nums[i] not in unique_nums:
            unique_nums.insert(0, nums[i])
    return unique_nums
```

*Alternate solution using a modified frequency map:*

```python
def remove_duplicates_from_front(nums):
    frequency_map = {}
    for num in nums:
        frequency_map[num] = True
    last_occurrences = []
    for num in nums[::-1]:  # Reverse iterate
        if frequency_map[num]:
            last_occurrences.append(num)
            frequency_map[num] = False
    return last_occurrences[::-1]  # Reverse again to original order
```