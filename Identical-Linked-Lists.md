*[[Unit 6 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 15 mins
* 🛠️ **Topics**: Linked Lists, Comparison
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: What if one list is longer than the other?
  - A: Then the lists cannot be identical, and the function should return False.

```markdown
HAPPY CASE
Input: List A = 1 -> 2 -> 3, List B = 1 -> 2 -> 3
Output: True
Explanation: Both lists have the same elements in the same order.

EDGE CASE
Input: List A = 1 -> 2 -> 3, List B = 1 -> 2
Output: False
Explanation: List B is shorter than List A; thus, they are not identical.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem is about list comparison, typically solved by traversing both lists simultaneously and comparing corresponding nodes.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Traverse both lists in tandem and compare each node's value.

```markdown
1) Initialize two pointers, each starting at the head of the respective lists.
2) Traverse both lists, comparing the values at each step.
3) If all corresponding nodes match and both lists end together, return True.
4) Return False if any mismatch is found or if the lists are of unequal length.
```

**⚠️ Common Mistakes**

- Assuming the lists are identical without checking if they end at the same time (i.e., one list could be longer).

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def is_identical(head_a, head_b):
    current_a = head_a
    current_b = head_b

    while current_a and current_b:
        if current_a.value != current_b.value:
            return False
        current_a = current_a.next
        current_b = current_b.next

    return current_a is None and current_b is None
```
 
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Use paired test cases to check for both True and False outputs under various conditions.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(min(m, n))` where `m` and `n` are the lengths of the two lists. The traversal stops as soon as the end of the shorter list is reached.
* **Space Complexity**: `O(1)` because the space usage does not depend on the input size, only a few pointers are used.
