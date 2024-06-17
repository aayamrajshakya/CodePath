*[[Unit 10 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 25 mins
* 🛠️ **Topics**: Hash Map, Pair Sum
    
## 1: U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- What should be returned if no such pair of integers exist?
    - An empty list `[]`.

```
HAPPY CASE
Input: numbers = [3, 4, 7, 1, 2, 9, 8]
Output: [3, 8, 4, 7]
Explanation: 3 + 8 = 4 + 7

HAPPY CASE
Input: numbers = [1, 2, 3, 4, 5]
Output: [1, 4, 2, 3]
Explanation: 1 + 4 = 2 + 3

EDGE CASE
Input: numbers = [1, 2, 3]
Output: []
Explanation: No such integers exist.

EDGE CASE
Input: numbers = []
Output: []
Explanation: The list is empty, so no such integers exist.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

For Pair Sum problems, we want to consider the following approaches:

- Using a hash map to track sums and corresponding pairs of numbers.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use a hash map to store the sum of pairs of numbers and their corresponding indices. If the same sum is found again, return the pairs of numbers. 

```
1) Initialize a hash map `map` to store sums and their corresponding pairs of numbers.
2) Iterate through each element `i` of the list `numbers`:
    a) Iterate through each element `j` from `i+1` to the end of the list:
        i) Calculate the sum of `numbers[i]` and `numbers[j]`.
        ii) If the sum is already in `map`, return the existing pair and the current pair as the result.
        iii) If the sum is not in `map`, store the sum with the pair `[numbers[i], numbers[j]]`.
3) If no such pair is found, return an empty list.
```

**⚠️ Common Mistakes**

- Not correctly handling cases where no such pairs exist.
- Incorrectly updating the hash map with pairs of numbers.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```
def find_sum_pair(numbers):
    length = len(numbers)
    map = {}

    for i in range(length):
        for j in range(i + 1, length):
            sum = numbers[i] + numbers[j]
            if sum in map:
                return map[sum] + [numbers[i], numbers[j]]
            else:
                map[sum] = [numbers[i], numbers[j]]
    return []
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with an input to check for the expected output.
- Example: Trace with numbers = [3, 4, 7, 1, 2, 9, 8]
    - Sum = 3 + 4 = 7, store [3, 4] in map
    - Sum = 3 + 7 = 10, store [3, 7] in map
    - Sum = 3 + 1 = 4, store [3, 1] in map
    - Sum = 3 + 2 = 5, store [3, 2] in map
    - Sum = 3 + 9 = 12, store [3, 9] in map
    - Sum = 3 + 8 = 11, store [3, 8] in map
    - Sum = 4 + 7 = 11, return [3, 8, 4, 7]

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

Assume `N` represents the length of the list `numbers`.

* **Time Complexity**: `O(N^2)` because we need to check all pairs of elements.
* **Space Complexity**: `O(N^2)` in the worst case for storing sums and their corresponding pairs in the hash map.