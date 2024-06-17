*[[Unit 4 Session 2]] (Click for link to problem statements)*

## U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What happens if k is equal to the length of the list?
  - If k is equal to the list length, the function should return just one element which is the average of the entire list.
- How does the function handle the case where k is greater than the list length?
  - This should ideally not occur given the constraint 1 ≤ k ≤ len(nums), but if it were to happen, the function would return an empty list as no such window could be formed.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Initialize a sliding window of size k. Compute the sum of the initial window then slide the window across the list while updating the sum and computing the new averages.

```markdown
1) Initialize an empty list `result` to store the average of each subarray.
2) Use two variables, `window_sum` to store the sum of elements in the current window, and `window_start` to indicate the start of the window.
3) Iterate through `arr` with a variable `window_end`:
  a) Add `arr[window_end]` to `window_sum`.
  b) If `window_end` is at least k - 1 (ensuring the window has reached size k):
     i) Append the average of the current window (`window_sum / k`) to `result`.
    ii) Subtract `arr[window_start]` from `window_sum` to remove the element that will be out of the window.
   iii) Increment `window_start` to slide the window right.
4) Return the list `result` containing all averages.
```

**⚠️ Common Mistakes**

- Not correctly adjusting the sum when the window slides which can lead to incorrect averages.
- Failing to handle edge cases where k equals 1 or the length of the array, though these should naturally be handled by the loop logic.

## I-mplement

```python
def find_averages_of_subarrays(k, arr):
    result = []
    window_sum, window_start = 0.0, 0
    for window_end in range(len(arr)):
        window_sum += arr[window_end]  # Add the next element to the window
        # Slide the window if we've hit the size 'k'
        if window_end >= k - 1:
            result.append(window_sum / k)  # Calculate the average
            window_sum -= arr[window_start]  # Remove the element going out
            window_start += 1  # Slide the window ahead
    return result
```