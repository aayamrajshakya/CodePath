*[[Unit 6 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 5 mins
* 🛠️ **Topics**: Linked List, Iteration
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: What should be returned if the linked list is empty?
    - A: The function returns `None` if the linked list is empty, indicating no maximum value can be determined.

```markdown
HAPPY CASE
Input: head = Node(10, Node(20, Node(30)))
Output: 30
Explanation: The list contains the integers 10, 20, and 30, with 30 being the maximum.

EDGE CASE
Input: head = None
Output: None
Explanation: An empty list has no elements to determine a maximum from.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This is a classic example of a traversal problem in linked lists where the goal is to identify the maximum value by examining each node’s data.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Traverse through each node of the linked list, keeping track of the highest value found so far.

```markdown
1) Start with the first node and initialize the maximum value to its value.
2) Traverse each node in the linked list.
3) Compare each node's value with the current maximum and update the maximum if a larger value is found.
4) Return the maximum value after the end of the list.
```

**⚠️ Common Mistakes**

- Returning an incorrect value when the list is empty.
- Not updating the maximum value correctly during traversal.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
class Node:
    def __init__(self, value, next=None):
        self.value = value
        self.next = next

def find_max(head):
    if not head:
        return None  # Handle the empty list case

    max_val = head.value  # Start max_val with the head's value
    current = head
    while current:
        if current.value > max_val:
            max_val = current.value  # Update max_val if current value is greater
        current = current.next
    
    return max_val  # Return the maximum value found
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Ensure the function returns the correct maximum or None when appropriate.
- Test with single-node lists to confirm they handle self-contained maximums correctly.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(n)` where `n` is the number of nodes in the linked list, since the algorithm must examine each node's value to find the maximum.
* **Space Complexity**: `O(1)` because the space used does not increase with the size of the input list. Only a few variables are used regardless of the list size.

