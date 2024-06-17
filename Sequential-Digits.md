*[[Unit 10 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 25 mins
* 🛠️ **Topics**: Number Generation, Iteration
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- What should be returned if there are no sequential digits in the given range?
    - An empty list `[]`.

```
HAPPY CASE
Input: low = 100, high = 300
Output: [123, 234]
Explanation: The numbers 123 and 234 have sequential digits and fall within the range.

HAPPY CASE
Input: low = 1000, high = 13000
Output: [1234, 2345, 3456, 4567, 5678, 6789, 12345]
Explanation: The numbers with sequential digits within the range are listed in ascending order.

EDGE CASE
Input: low = 10, high = 10
Output: []
Explanation: The number 10 does not have sequential digits.

EDGE CASE
Input: low = 5, high = 5
Output: []
Explanation: The number 5 does not have sequential digits.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

For problems involving number generation, we want to consider the following approaches:

- Generating numbers that meet the criteria and checking if they fall within the given range.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Generate all possible sequential digit numbers and check if they fall within the given range.

```
1) Initialize an empty list `result` to store the numbers with sequential digits.
2) Iterate through each starting digit from 1 to 9:
    a) Initialize `num` with the starting digit.
    b) Initialize `next_digit` with the starting digit.
    c) While `num` is less than or equal to `high` and `next_digit` is less than 10:
        i) If `num` is greater than or equal to `low`, add `num` to `result`.
        ii) Increment `next_digit`.
        iii) Update `num` to be `num * 10 + next_digit`.
3) Return the `result` list.
```

**⚠️ Common Mistakes**

- Not correctly generating the sequential digits.
- Not checking if the generated number falls within the given range.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```
def sequential_digits(low, high):
    result = []
    
    # Generate all possible sequential digit numbers
    for start in range(1, 10):
        num = start
        next_digit = start
        while num <= high and next_digit < 10:
            if num >= low:
                result.append(num)
            next_digit += 1
            num = num * 10 + next_digit
    
    # The numbers are generated in order, so no need to sort explicitly
    return result
```
 
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with an input to check for the expected output.
- Example: Trace with low = 100, high = 300
    - Generate numbers: 123, 234 within range and add to result
    - Return result = [123, 234]

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

Assume `N` represents the number of digits in the largest number within the given range.

* **Time Complexity**: `O(1)` because the number of possible sequential digits is constant and does not depend on the input range.
* **Space Complexity**: `O(1)` because the maximum space needed to store the result is also constant.