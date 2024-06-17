*[[Unit 6 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 10 mins
* 🛠️ **Topics**: Linked Lists, Circular Linked Lists
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: What if the linked list is empty?
  - A: Return None since there is no node to point to itself.

```markdown
HAPPY CASE
Input: 1 -> 2 -> 3
Output: 1 -> 2 -> 3 -> 1 (circular)
Explanation: The last node (3) now points to the head of the list (1), making it circular.

EDGE CASE
Input: None (Empty list)
Output: None
Explanation: Since the list is empty, it remains empty as circular doesn't apply.
```
  
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem involves making a singly linked list circular, which typically involves traversing to the end of the list and connecting the last node to the head.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Traverse the list to find the last node and link it back to the head to form a circular structure.

```markdown
1) Start at the head of the list.
2) If the head is None, return None immediately.
3) Traverse to the last node of the list.
4) Set the next of the last node to the head to make the list circular.
5) Return the head of the list as it is now the entry point to the circular list.
```

**⚠️ Common Mistakes**

- Forgetting to handle the empty list case, which should simply return None.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def make_circular(head):
    if not head:
        return None  # If the list is empty, return None
    
    current = head
    while current.next:
        current = current.next
    
    current.next = head
    return head
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Test the code with a typical non-empty list to ensure it becomes circular.
- Test with an empty list to ensure it returns None.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(n)` where `n` is the length of the list. We traverse the list once to find the last node.
* **Space Complexity**: `O(1)` as no additional space is needed beyond pointers for traversal.
