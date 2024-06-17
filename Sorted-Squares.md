*[[Unit 4 Session 2]] (Click for link to problem statements)*

## U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What should the function do with negative numbers?
  - The function should square each number, which eliminates the sign, and still return the results in sorted order.
- How does the function handle an empty list?
  - If the input list is empty, the function should return an empty list as there are no numbers to square.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use a two-pointer approach starting from both ends of the list to efficiently square and place the squared values in order into a result list.

```markdown
1) Initialize two pointers, `left` at the start and `right` at the end of the list.
2) Create a result list initialized with zeroes, the same size as the input list.
3) Iterate over the input list from the end to the beginning:
  a) Compare the absolute values of the elements at `left` and `right`.
  b) Square the larger absolute value and place it in the current position in the result list.
  c) Move the pointer corresponding to the larger absolute value towards the center.
4) Return the filled result list.
```

**⚠️ Common Mistakes**

- Squaring the values without considering the absolute values, which could mess up the order when negatives are involved.
- Incorrectly handling the pointer updates, leading to wrong placements or missed elements.

## I-mplement

```python
def sorted_squares(nums):
    left, right = 0, len(nums) - 1
    result = [0] * len(nums)
    for i in range(len(nums) - 1, -1, -1):
        if abs(nums[left]) > abs(nums[right]):
            square = nums[left] ** 2
            left += 1
        else:
            square = nums[right] ** 2
            right -= 1
        result[i] = square
    return result
```