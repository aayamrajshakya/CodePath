*[[Unit 4 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What are the main differences between the two-pointer and dict methods in terms of algorithm efficiency?

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**Two-pointer method:**
```markdown
- **Time Complexity:** O(n) because each element is potentially visited once by either pointer before finding a solution or reaching the convergence point.
- **Space Complexity:** O(1) since it modifies the input list in place without using extra storage.
```
Dict method:
```markdown
- **Time Complexity:** O(n) since it processes each element exactly once but uses a dict to store previous values for constant-time look-up.
- **Space Complexity:** O(n) as it needs to potentially store each element and its index in the dict.
```

**Comparison:**

**Time Complexity:** Both methods operate in O(n) time, but the two-pointer method requires the list to be sorted beforehand, which could entail additional preprocessing if not already sorted.

**Space Complexity:** The two-pointer method is more space-efficient (O(1)) compared to the dict method (O(n)).

## I-mplement

```python
# NON TWO POINTER
# Time complexity: O(n)
# Space complexity: O(n)
def two_sum(nums, target):
    prev_map = {}  # O(n) space complexit
    
    for i in range(len(nums)): # O(n) time complexity
        diff = target - nums[i]
        if diff in prev_map:
            return [prev_map[diff], i]
        prev_map[nums[i]] = i
        
# TWO POINTER
# Time complexity: O(n)
# Space complexity: O(1)
def two_sum(nums, target):
    left = 0
    right = len(nums) - 1
    
    while left < right: # O(n) time complexity
        current_sum = nums[left] + nums[right]
        if current_sum == target:
            return [left, right] 
        elif current_sum < target:
            left += 1  # Need a larger sum
        else:
            right -= 1  # Need a smaller sum  
```

**Takeaway**
- When considering space limitations, the two-pointer solution is preferred due to its minimal space usage. However, it assumes a sorted input, which may not always be applicable.