*[[Unit 4 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What do we do if there are multiple pairs that could work but we only need one?
  - Since the problem guarantees exactly one solution, this situation will not occur.
- What if the list has negative numbers?
  - The approach still works as the list is sorted, allowing the two-pointer technique to be effective regardless of the sign of the numbers.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use two pointers to find two numbers that add up to the target by adjusting their positions based on the sum comparison to the target.

```markdown
1) Initialize two pointers: `left` at the start of the list and `right` at the end.
2) While the `left` pointer is less than the `right` pointer:
  a) Calculate the `current_sum` of the numbers at the two pointers.
  b) If `current_sum` equals `target`, return the indices `[left, right]`.
  c) If `current_sum` is less than `target`, increment the `left` pointer to try a larger sum.
  d) If `current_sum` is greater than `target`, decrement the `right` pointer to try a smaller sum.
3) Since the problem guarantees a solution, the loop will always return before it terminates.
```

**⚠️ Common Mistakes**

- Forgetting to move the pointers correctly based on the comparison results could lead to infinite loops or missing the correct answer.

## I-mplement

```python
def two_sum(nums, target):
    left = 0
    right = len(nums) - 1
    
    while left < right:
        current_sum = nums[left] + nums[right]
        if current_sum == target:
            return [left, right] 
        elif current_sum < target:
            left += 1  # Need a larger sum
        else:
            right -= 1  # Need a smaller sum
```