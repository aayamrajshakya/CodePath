*[[Unit 4 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What happens if all numbers are even or all are odd?
  - The function should handle these cases gracefully without making unnecessary swaps.
- Should the function also sort the numbers within the even and odd groups?
  - No, the task is only to separate evens and odds, sorting them further is not needed.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use a two-pointer approach to separate even and odd numbers in the list.

```markdown
1) 1) Initialize two pointers: `left` at the start and `right` at the end of the list.
2) While `left` is less than `right`:
  a) If the number at `left` is even, move `left` pointer one step to the right.
  b) If the number at `right` is odd, move `right` pointer one step to the left.
  c) If the number at `left` is odd and the number at `right` is even, swap them, then move both pointers.
3) Return the modified list.
```

**⚠️ Common Mistakes**

- Failing to check the correct conditions before moving the pointers can lead to infinite loops or incorrect results.
- Overlooking the importance of updating both pointers after a swap to avoid re-evaluating the same elements.

## I-mplement

```python
def sort_array_by_parity(nums):
    left, right = 0, len(nums) - 1
    
    while left < right:
        # Move left pointer forward if current number is even
        if nums[left] % 2 == 0:
            left += 1
        # Move right pointer backward if current number is odd
        elif nums[right] % 2 != 0:
            right -= 1
        # Swap when left pointer points to an odd number and right pointer points to an even number
        else:
            nums[left], nums[right] = nums[right], nums[left]
            left += 1
            right -= 1
    
    return nums
```