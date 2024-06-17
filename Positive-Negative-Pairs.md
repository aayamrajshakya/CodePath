*[[Unit 4 Session 2]] (Click for link to problem statements)*

## U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What happens if the list is empty?
  - If the list is empty, the function should return -1, as there are no elements to consider.
- How should the function handle large lists or extreme values?
  - The function handles sorting efficiently and checks pairs from the ends of the list, so it should perform well even with large lists or extreme values.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** First, sort the list of numbers. Then use a two-pointer technique to find pairs where one is the negative of the other, updating the largest such positive integer found.

```markdown
1) Sort the list of integers.
2) Initialize two pointers at the beginning and end of the sorted list.
3) Initialize a variable to keep track of the largest valid k found, start with -1.
4) While the left pointer is less than the right pointer:
  a) Calculate the sum of the values at the two pointers.
  b) If the sum is less than 0, move the left pointer right to find a less negative number.
  c) If the sum is more than 0, move the right pointer left to find a smaller positive number.
  d) If the sum is 0, update the largest k if the current k (value at the right pointer) is greater than the current largest k.
     Then move both pointers to continue searching.
5) Return the largest k found or -1 if no such pair exists.
```

**⚠️ Common Mistakes**

- Forgetting to sort the array before applying the two-pointer technique could result in failing to find valid pairs.
- Not updating the largest k correctly when a valid pair is found.

## I-mplement

```python
def findLargestK(nums):
    nums.sort()  # Step 1
    left, right = 0, len(nums) - 1
    largestK = -1  # Initialize largestK with -1
    
    while left < right:  # Ensure we do not cross pointers
        sum = nums[left] + nums[right]
        
        if sum < 0:  # The negative number is too small (too negative)
            left += 1
        elif sum > 0:  # The positive number is too large
            right -= 1
        else:  # Found a pair
            largestK = nums[right]  # Update largestK
            left += 1
            right -= 1
    
    return largestK
```