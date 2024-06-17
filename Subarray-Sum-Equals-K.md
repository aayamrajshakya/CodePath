*[[Unit 10 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 30 mins
* 🛠️ **Topics**: Array, Hashing, Prefix Sum
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- What should be returned if `nums` is empty?
    - 0, since there are no subarrays to sum up to `k`.

```
HAPPY CASE
Input: nums = [1, 1, 1], k = 2
Output: 2
Explanation: The subarrays [1, 1] (starting at index 0) and [1, 1] (starting at index 1) sum to 2.

HAPPY CASE
Input: nums = [1, 2, 3], k = 3
Output: 2
Explanation: The subarrays [1, 2] and [3] sum to 3.

EDGE CASE
Input: nums = [], k = 0
Output: 0
Explanation: The array is empty, so the output is 0.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

For Array problems involving subarrays and sums, we want to consider the following approaches:

- Using a hash map to store the cumulative sums and their frequencies to find the subarrays that sum to `k`.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use a hash map to store the cumulative sums and their frequencies. Iterate through the array, maintaining the current cumulative sum. For each element, check if the cumulative sum minus `k` exists in the hash map. If it does, add the frequency of this sum to the count. Update the hash map with the current cumulative sum.

```
1) Initialize a hash map `cumulative_sum` with a default value of 0 for the cumulative sum 0.
2) Initialize `current_sum` to 0 and `count` to 0.
3) Iterate through each element `num` in the array `nums`:
    a) Add `num` to `current_sum`.
    b) If `current_sum` is equal to `k`, increment `count`.
    c) If `current_sum - k` exists in `cumulative_sum`, add its frequency to `count`.
    d) Update `cumulative_sum` with `current_sum`.
4) Return `count`.
```

**⚠️ Common Mistakes**

- Forgetting to handle the case where the array is empty.
- Not correctly updating the hash map with cumulative sums.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```
def subarray_sum(nums, k):
    cumulative_sum = {0: 1}
    current_sum = 0
    count = 0
    
    for num in nums:
        current_sum += num
        
        if current_sum == k:
            count += 1
        
        if current_sum - k in cumulative_sum:
            count += cumulative_sum[current_sum - k]
        
        if current_sum in cumulative_sum:
            cumulative_sum[current_sum] += 1
        else:
            cumulative_sum[current_sum] = 1
    
    return count
```
 
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with an input to check for the expected output.
- Example: Trace with nums = [1, 1, 1], k = 2
    - current_sum = 1, cumulative_sum = {0: 1, 1: 1}
    - current_sum = 2, cumulative_sum = {0: 1, 1: 1, 2: 1}, count = 1
    - current_sum = 3, cumulative_sum = {0: 1, 1: 1, 2: 1, 3: 1}, count = 2
    - Return count = 2

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

Assume `N` represents the length of the array `nums`.

* **Time Complexity**: `O(N)` because we need to iterate through the array once.
* **Space Complexity**: `O(N)` because we need to store the cumulative sums in a hash map.