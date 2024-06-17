*[[Unit 10 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 15 mins
* 🛠️ **Topics**: String, Simulation
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- What should be returned if `currentState` does not contain any `"++"`?
    - An empty list `[]`, as there are no valid moves.

```
HAPPY CASE
Input: currentState = "++++"
Output: ["--++", "+--+", "++--"]
Explanation: There are three possible moves by flipping two consecutive "++" into "--".

HAPPY CASE
Input: currentState = "++--"
Output: ["----"]
Explanation: There is one possible move by flipping two consecutive "++" into "--".

EDGE CASE
Input: currentState = "----"
Output: []
Explanation: There are no "++" in the string, so no valid moves can be made.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

For String problems, we want to consider the following approaches:

- Using a loop to iterate through the string and check for consecutive "++" substrings.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Iterate through the string, and whenever two consecutive "++" are found, replace them with "--" and add the new state to the result list.

```
1) Initialize an empty list `result` to store possible states.
2) Iterate through the string `current_state` using a loop:
    a) Check if the current character and the next character are both '+'.
    b) If they are, create a new state by replacing "++" with "--" and add it to `result`.
3) Return the `result` list.
```

**⚠️ Common Mistakes**

- Not handling cases where there are no consecutive "++" substrings.
- Incorrectly updating the string when generating new states.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```
def generate_possible_next_moves(current_state):
    result = []
    for i in range(len(current_state) - 1):
        if current_state[i] == '+' and current_state[i + 1] == '+':
            new_state = current_state[:i] + '--' + current_state[i + 2:]
            result.append(new_state)
    return result
```
 
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with an input to check for the expected output.
- Example: Trace with currentState = "++++"
    - result = []
    - i = 0, new_state = "--++", result = ["--++"]
    - i = 1, new_state = "+--+", result = ["--++", "+--+"]
    - i = 2, new_state = "++--", result = ["--++", "+--+", "++--"]
    - Return result = ["--++", "+--+", "++--"]

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

Assume `N` represents the length of the string `current_state`.

* **Time Complexity**: `O(N)` because we need to iterate through the string once.
* **Space Complexity**: `O(N)` because we need to store the result list.