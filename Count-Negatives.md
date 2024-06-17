*[[Unit 4 Session 2]] (Click for link to problem statements)*

## U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What happens if k is greater than the length of the list?
  - If k is greater than the list length, the function should return an empty list as no sublists of size k can be formed.
- How does the function handle cases where all numbers are positive?
  - If all numbers are positive, each element in the returned list should be 0, indicating no negative numbers in any sublist.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Implement a sliding window to count negative numbers within each window of size k in the list.

```markdown
1) Initialize a list `result` to store the count of negative numbers for each window.
2) Use a pointer `start` to denote the beginning of each window.
3) Initialize a variable `count` to keep track of the number of negative numbers in the current window.
4) Iterate over the list using an index `i`:
  a) If the current number is negative, increase the `count`.
  b) When the window size reaches k (i.e., i - start + 1 == k):
     i) Append `count` to `result`.
    ii) If the number at the `start` of the window is negative, decrease the `count`.
   iii) Increment `start` to slide the window right.
5) Return the `result` list.
```

**⚠️ Common Mistakes**

- Forgetting to decrement the count of negatives when sliding the window and removing a negative number.
- Incorrectly initializing or updating the `start` index, leading to windows of incorrect size.

## I-mplement

```python
def count_negatives(lst, k):
    result = []
    start = 0
    count = 0
    
    for i in range(len(lst)):
        if lst[i] < 0:
            count += 1
        
        if (i - start + 1 == k):
            result.append(count)
            if lst[start] < 0:
                count -= 1
                
            start += 1
    
    return result
```