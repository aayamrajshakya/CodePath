*[[Unit 7 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 10 mins
* 🛠️ **Topics**: Recursion, List Operations, Product Calculation
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: What should the function return for an empty list?
  - A: The function should return 1 for an empty list, as the product of no elements is typically considered 1 (neutral element for multiplication).

```
HAPPY CASE
Input: [1, 2, 3, 4, 5]
Output: 120
Explanation: The product of all elements in the list is 1 * 2 * 3 * 4 * 5 = 120.

EDGE CASE
Input: []
Output: 1
Explanation: An empty list returns a product of 1.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem is a typical example of using recursion for aggregation:

- Recursive decomposition to calculate a product.
- Handling base cases in recursion to correctly terminate and aggregate results.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Develop a recursive function that calculates the product of all values in a list by recursively multiplying the first element by the product of the remaining list.

```markdown
1) Base Case: If the list is empty, return 1.
2) Recursive Case: Return the first element multiplied by the recursive call for the rest of the list.
```

**⚠️ Common Mistakes**

- Forgetting the base case which might lead to an error when trying to access elements of an empty list.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def list_product(lst):
    if not lst:
        return 1
    else:
        return lst[0] * list_product(lst[1:])
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with an input of [1, 2, 3, 4, 5] to check for the expected output of 120.
- Validate the base case with an empty list to ensure it returns 1.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(n)` because each function call processes one element of the list.
* **Space Complexity**: `O(n)` due to the recursion depth being equal to the number of elements in the list.
