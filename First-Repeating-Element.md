*[[Unit 2 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What if the list is empty?
  - In this case, return `None`.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Loop through the list, keeping track of what index we FIRST saw an element at.  When we see an element twice, keep track of the lowest index so far.

```markdown
1) Create an empty dict to store first occurrence of indices
2) Initialize min_index to None
3) For each index in nums:
  a) If we haven't seen this num before, store its index in the dict
  b) If it's already in the dict, it's a duplicate!
     i) If it's first-seen index is smaller than our min_index, update min_index
4) Return min_index
```

**⚠️ Common Mistakes**

- Make sure you are returning the FIRST index the repeating element appears at -- not the index where you found the second element.

## I-mplement

```python
def find_min_index_of_repeating(nums):
    # Dictionary to store the first occurrence index of elements
    first_occurrence = {}
    min_index = None  # Initialize min_index to impossible value
    
    for i in range(len(nums)):
        if nums[i] not in first_occurrence:
            first_occurrence[nums[i]] = i
        elif min_index is None or first_occurrence[nums[i]] < min_index:
            min_index = first_occurrence[nums[i]]
            
    return min_index
```

*Alternate right-to-left solution:*
```python
def find_min_index_of_repeating(nums):
    # Dictionary to store the first occurrence index of elements
    first_occurrence = {}
    min_index = None  # Initialize min_index to infinity
    
    # Traverse the list from right to left to ensure the minimum index of the first repeating element is found
    for i in range(len(nums)-1, -1, -1):
        if nums[i] in first_occurrence:
            # If the element is found in the dictionary, update min_index if necessary
            min_index = i
        else:
            # Store the index of the first occurrence
            first_occurrence[nums[i]] = i
    
    return min_index
```