*[[Unit 6 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 15 mins
* 🛠️ **Topics**: Linked Lists
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What if the linked list only contains one node?
  - If the single node points to itself, the function should return True; otherwise, it should return False.
- What if the linked list is empty?
  - An empty list is not circular by definition so the function should return False.

```markdown
HAPPY CASE
Input: A list where the last node points back to the first node (e.g., num1 -> num2 -> num3 -> num1)
Output: True
Explanation: The tail node points back to the head, forming a circular linked list.

EDGE CASE
Input: A single node that does not point to itself (e.g., num1)
Output: False
Explanation: The single node points to None, indicating it is not a circular linked list.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

For Circular Linked List detection problems, we want to consider the following approaches:

- Traversing from head to tail and checking if tail points back to head. A circular linked list should not have any node pointing to None.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Start at the head and traverse the list, checking if the tail points back to the head.

```markdown
1) Start at the head.
2) If the list is empty, return False.
3) Traverse through the list. If any node points back to the head, return True.
4) If the end of the list is reached (i.e., current.next is None), return False.
```

**⚠️ Common Mistakes**

- Not handling the empty list case.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def is_circular(head):
    if not head:
        return False  # An empty list is not circular by definition
    
    current = head
    while current.next:
        current = current.next
        if current.next == head:
            return True  # Found that tail points back to head

    return False
```
    
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with the happy case to ensure correct output.
- Check with an edge case to verify handling of non-circular single node.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(n)` where `n` is the number of nodes in the linked list. The entire list is traversed in the worst case.
* **Space Complexity**: `O(1)` as no extra space is used other than a few variables for tracking nodes.
