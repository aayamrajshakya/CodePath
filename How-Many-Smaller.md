*[[Unit 2 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Does the order of my output matter?
  - Yes.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** First, sort the list from smallest to largest.  When sorted, the lowest index a value appears at will ALSO be the number of elements smaller.  Finally, put the results back in the original order.

```markdown
1) Create a sorted copy of the nums list
2) Create an empty dict to store value : smaller counts.
3) For each index in nums
  a) If the value at index is not in our dict, map value -> index
  b) Otherwise, skip, as this is a duplicate of a value we've already checked
4) Create an empty list to store the results in their original order
5) For each number in the original list (not sorted list)
  a) Use the dict to lookup the count for that number
  b) Add that count value to our results list
6) Return the results list
```

**⚠️ Common Mistakes**

- In order to return the values to their original order, you will need to keep track of both a sorted and an original version of the list!

## I-mplement

```python
def smallerNumbersThanCurrent(nums):
    # Sort the nums list
    sorted_nums = sorted(nums)
    
    # Dictionary to store the smallest index at which each number appears
    smaller_count_map = {}
    for i in range(len(sorted_nums)):
        num = sorted_nums[i]
        # Only set the index for the first occurrence of each number
        if num not in smaller_count_map:
            smaller_count_map[num] = i
    
    # Manually generate the result based on the original list values
    result = []
    for num in nums:
        result.append(smaller_count_map[num])
    
    return result
```