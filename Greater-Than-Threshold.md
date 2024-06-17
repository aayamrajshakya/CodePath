*[[Unit 4 Session 2]] (Click for link to problem statements)*

## U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What happens if the list is smaller than k?
  - The function should return 0 as no subarrays of size k can be formed.
- How does the function handle negative numbers in `nums`?
  - Negative numbers are treated the same as positive numbers in terms of summing for averages; they will contribute to the total window sum, potentially reducing the number of qualifying windows.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use a sliding window of size k to calculate the sum of subarrays. Compare each window's sum to the minimum sum required (calculated as `threshold * k`) to determine if it meets or exceeds the threshold average.

```markdown
1) Calculate the `threshold_sum` which is the minimum sum required for a window to meet the average threshold.
2) Initialize a counter `count` to track the number of qualifying subarrays.
3) Compute the sum of the first window of size k.
4) Check if this initial window meets or exceeds the `threshold_sum`.
5) Slide the window across the list by adding the next element and subtracting the element that leaves the window.
6) For each new window configuration, check if it meets or exceeds the `threshold_sum`.
7) Increment the counter each time a window meets the conditions.
8) Return the counter value.
```

**⚠️ Common Mistakes**

- Incorrectly calculating the initial window sum or failing to update it correctly when sliding the window.
- Not checking all windows, especially the first and last possible windows, due to incorrect loop conditions or initialization.

## I-mplement

```python
def num_of_subarrays(lst, k, threshold):
    # Calculate the total sum needed to meet or exceed the threshold for a window
    threshold_sum = threshold * k
    count = 0
    window_sum = sum(lst[:k])  # Sum of the first window of size k

    # Check if the first window meets the condition
    if window_sum >= threshold_sum:
        count += 1

    # Slide the window across the array
    for i in range(k, len(lst)):
        window_sum += lst[i] - lst[i-k]  # Update the window sum
        if window_sum >= threshold_sum:  # Check the condition for the current window
            count += 1

    return count
```