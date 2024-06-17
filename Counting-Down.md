*[[Unit 7 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 10 mins
* 🛠️ **Topics**: Recursion, Iteration, Function comparison
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: What happens if the countdown starts from a negative number?
  - A: For simplicity, we can assume the countdown always starts from a positive number or zero.

```
HAPPY CASE
Input: 5
Output: "5 4 3 2 1"
Explanation: The countdown from 5 should print numbers decrementing to 1.

EDGE CASE
Input: 0
Output: (nothing printed)
Explanation: A countdown starting at 0 should not print any numbers.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This task relates to basic control structures in programming, focusing on:

- Converting recursion to an iterative solution.
- Ensuring the output matches in terms of format and content.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Convert a recursive function that counts down numbers to an iterative approach using a loop.

```markdown
1) Define a function `countdown_iterative(n)` that initializes a loop starting from n down to 1.
2) Inside the loop, print the current number.
3) Ensure that no output is produced for n <= 0 to match the recursive behavior.
```

**⚠️ Common Mistakes**

- Not handling the case of `n = 0` correctly, which should result in no output.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def countdown_iterative(n):
    for i in range(n, 0, -1):
        print(i)
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with an input of 5 to check for the expected output of "5 4 3 2 1".
- Validate that input 0 results in no output, correctly handling the edge case.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(n)` because the loop iterates from n down to 1.
* **Space Complexity**: `O(1)` because no additional space is used beyond the loop control variable.
