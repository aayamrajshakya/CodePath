*[[Unit 4 Session 2]] (Click for link to problem statements)*

## U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- How does the function handle the scenario where all elements are greater than or equal to the target?
  - If all elements in the list, when summed with any other, exceed the target, the function should return 0 as no valid pairs meet the condition.
- What happens if the list is empty or contains only one element?
  - In cases where the list is empty or contains only one element, the function should return 0 as there are no possible pairs.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Sort the list to facilitate the use of a two-pointer technique where one pointer starts from each element and the other searches for the upper limit where their sum is less than the target.

```markdown
1) Sort the list of numbers to allow ordered comparisons.
2) Initialize a counter to track the number of valid pairs.
3) Iterate through the list with a pointer `left` starting from the first element.
4) For each element at `left`, initiate a second pointer `right` from `left + 1`.
5) Use a while loop to move `right` while `nums[left] + nums[right]` is less than the target.
6) After exiting the loop for each `left`, calculate the number of valid pairs by subtracting `left + 1` from `right` and add to the count.
7) Return the total count of pairs.
```

**⚠️ Common Mistakes**

- Incorrect loop condition or incorrect update of the `right` pointer could lead to missing valid pairs or counting invalid pairs.
- Miscounting the number of valid pairs by not adjusting for the indices properly.

## I-mplement

```python
def count_pairs(nums, target):
    nums.sort()  # Sort the array to use two pointers
    count = 0
    n = len(nums)

    for left in range(n):
        right = left + 1
        while right < n and nums[left] + nums[right] < target:
            right += 1
        count += right - left - 1  # Add the number of valid pairs with nums[left]

    return count
```