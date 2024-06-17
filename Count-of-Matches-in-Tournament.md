*[[Unit 10 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 15 mins
* 🛠️ **Topics**: Simulation, Math
    
## 1: U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- What should be returned if `n` is 1?
    - 0, since no matches are needed when there is only one team.

```
HAPPY CASE
Input: n = 7
Output: 6
Explanation: 7 teams participate. In the first round, 6 matches are played, leaving 4 teams (since one team advances randomly). In the second round, 2 matches are played, leaving 2 teams. In the final round, 1 match is played. In total, 6 + 2 + 1 = 9 matches are played.

HAPPY CASE
Input: n = 8
Output: 7
Explanation: 8 teams participate. In the first round, 4 matches are played, leaving 4 teams. In the second round, 2 matches are played, leaving 2 teams. In the final round, 1 match is played. In total, 4 + 2 + 1 = 7 matches are played.

EDGE CASE
Input: n = 1
Output: 0
Explanation: Only one team is present, so no matches are needed.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

For Tournament problems, we want to consider the following approaches:

- Simulating the matches played and counting them until only one team remains.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Iterate until only one team remains, counting the matches played at each round.

```
1) Initialize total_matches to 0.
2) While n is greater than 1:
    a) If n is even, the number of matches is n / 2, and n becomes n / 2.
    b) If n is odd, the number of matches is (n - 1) / 2, and n becomes (n - 1) / 2 + 1.
    c) Add the number of matches to total_matches.
3) Return total_matches.
```

**⚠️ Common Mistakes**

- Not correctly handling the case where the number of teams is odd.
- Incorrectly updating the number of teams after each round.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```
def number_of_matches(n):
    total_matches = 0
    while n > 1:
        if n % 2 == 0:
            matches = n // 2
            n = n // 2
        else:
            matches = (n - 1) // 2
            n = (n - 1) // 2 + 1
        total_matches += matches
    return total_matches
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with an input to check for the expected output.
- Example: Trace with n = 7
    - Round 1: 6 matches, 4 teams
    - Round 2: 2 matches, 2 teams
    - Round 3: 1 match, 1 team
    - Total matches = 6 + 2 + 1 = 9

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

Assume `N` represents the number of teams.

* **Time Complexity**: `O(log N)` because we halve the number of teams at each step.
* **Space Complexity**: `O(1)` because we only use a constant amount of extra space.