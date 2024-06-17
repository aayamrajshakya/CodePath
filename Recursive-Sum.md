*[[Unit 7 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 10 mins
* 🛠️ **Topics**: Recursion, Lists, Summation
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: How should the function handle an empty list?
  - A: The function should return 0 for an empty list, as the sum of no elements is 0.

```
HAPPY CASE
Input: [1, 2, 3, 4, 5]
Output: 15
Explanation: The sum of the list elements is 1 + 2 + 3 + 4 + 5 = 15.

EDGE CASE
Input: []
Output: 0
Explanation: An empty list returns a sum of 0.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem matches typical recursion patterns where the solution involves:

- Breaking down the problem into smaller parts by considering one element at a time.
- Using recursion to sum the rest of the list.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use a recursive approach to sum elements of the list, reducing the list size by one with each recursive call.

```markdown
1) Base Case: If the list is empty, return 0.
2) Recursive Case: Return the first element of the list plus the result of a recursive call to `sum_list()` with the rest of the list.
```

**⚠️ Common Mistakes**

- Not handling the base case correctly, which could lead to an error or infinite recursion.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def sum_list(lst):
    if len(lst) == 0:
        return 0
    else:
        return lst[0] + sum_list(lst[1:])
```
    
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with an input of [1, 2, 3, 4, 5] to check that each element is added correctly, resulting in 15.
- Ensure that passing an empty list results in 0, correctly handling the edge case.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(n)` because we need to process each element in the list once.
* **Space Complexity**: `O(n)` due to the recursion stack depth being proportional to the list size.
