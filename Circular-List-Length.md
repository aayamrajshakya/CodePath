*[[Unit 6 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 10 mins
* 🛠️ **Topics**: Circular Linked Lists, Traversal
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: What if the circular linked list consists of only one node?
  - A: The length should return 1, as it has only one node, even though it points to itself.

```markdown
HAPPY CASE
Input: 1 -> 2 -> 3 -> 1
Output: 3
Explanation: There are three nodes in the circular list.

EDGE CASE
Input: 1 -> 1
Output: 1
Explanation: The list contains only one node that points to itself.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem is about calculating the length of a circular linked list, which involves traversing the list until the start point is reached again.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Start at the head and count nodes until the list loops back to the starting point.

```markdown
1) Start at the head and initialize a count variable.
2) Traverse the list, incrementing the count until you return to the starting node.
3) Return the count.
```

**⚠️ Common Mistakes**

- Not correctly handling the loop detection, which could lead to infinite loops if not careful.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def circular_list_length(head):
    if not head:
        return 0  # An empty list has a length of 0
    
    current = head
    count = 0
    while True:
        count += 1
        current = current.next
        if current == head:
            break  # Once we loop back to the head, we've seen all nodes
    
    return count
```
 
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Test the function with a standard circular list to ensure accurate counting.
- Validate the function with a single-node circular list to check for correct length determination.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(n)` where `n` is the number of nodes in the list, as each node is visited once.
* **Space Complexity**: `O(1)` as no additional space is required beyond temporary variables.
