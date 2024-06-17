*[[Unit 7 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 5 mins
* 🛠️ **Topics**: Recursion, Iteration, Function comparison
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: What output is expected when `n = 0`?
  - A: The function should print nothing, indicating no recursive or iterative calls.

HAPPY CASE
Input: 5
Output: "Hello" printed 5 times
Explanation: Both recursive and iterative versions print "Hello" 5 times for an input of 5.

EDGE CASE
Input: 0
Output: (nothing printed)
Explanation: When `n` is 0, neither the recursive nor iterative function should produce any output.
```
   
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

For recursion versus iteration problems, we typically consider the following approaches:

- Understanding the equivalence in iteration through recursion and loops.
- Converting recursive logic to iterative logic using stacks or simple loops.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Convert a simple recursive function that prints "Hello" n times into an iterative version that achieves the same outcome without recursion.

```markdown
1) Define a function `repeat_hello_iterative(n)` that initializes a loop from 0 to n.
2) Inside the loop, print "Hello".
3) Call `repeat_hello_iterative()` with the test values to ensure it mimics `repeat_hello()` behavior.
```

**⚠️ Common Mistakes**

- Not accounting for the case when `n` is 0, which should result in no output.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def repeat_hello_iterative(n):
    for i in range(n):
        print("Hello")
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with an input of 5 to check for the expected output of five "Hello" prints.
- Ensure that passing 0 results in no output, correctly handling the edge case.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(n)` because the loop runs n times, where n is the input number.
* **Space Complexity**: `O(1)` because no additional space is used; the only memory used is for the loop counter.
