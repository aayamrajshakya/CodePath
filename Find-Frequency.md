*[[Unit 6 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 15 mins
* 🛠️ **Topics**: Linked Lists
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: How should the function handle an empty linked list?
    - A: The function should return 0 if the linked list is empty since there would be no instances of the value.

```markdown
HAPPY CASE
Input: [1, 2, 3, 4, 3, 3], 3
Output: 3
Explanation: The value 3 appears three times in the linked list.

EDGE CASE
Input: [], 5
Output: 0
Explanation: The linked list is empty, so the frequency of any value is 0.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

For Linked List problems, we want to consider the following approaches:

- Traverse the list while counting occurrences of a specific value.
- Use a simple iterative method to handle each node until the end is reached.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Iterate through the linked list, comparing each node's value to the target value, incrementing a counter if they match.

```markdown
1) Start with the head of the list.
2) Initialize a counter to zero.
3) Traverse the list:
    - Compare the current node's value with the target value.
    - If they match, increment the counter.
    - Move to the next node.
4) Return the counter value after traversing the entire list.
```

**⚠️ Common Mistakes**

- Forgetting to handle the case where the linked list is empty.
- Not updating the current node to the next node in the loop, which would cause an infinite loop.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def count_element(head, val):
    count = 0  # Initialize a counter for the occurrences
    current = head  # Start with the head of the list
    
    while current:
        if current.value == val:
            count += 1  # Increment count if the current node's value matches val
        current = current.next  # Move to the next node
    
    return count  # Return the total count of occurrences
```
  
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with an input to check for the expected output
- Catch possible edge cases and off-by-one errors

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

Assume `N` represents the number of nodes in the linked list.

* **Time Complexity**: `O(N)` because we need to traverse each node in the linked list to check for the value.
* **Space Complexity**: `O(1)` because we use only a fixed amount of space regardless of the input size.
