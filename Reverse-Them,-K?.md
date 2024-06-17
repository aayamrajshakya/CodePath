*[[Unit 6 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 20 mins
* 🛠️ **Topics**: Linked Lists, Reversal
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: What happens when k is 0 or the list is empty?
    - A: If k is 0, the list remains unchanged. If the list is empty, return `None`.

```markdown
HAPPY CASE
Input: Head = 1 -> 2 -> 3 -> 4 -> 5, k = 3
Output: 3 -> 2 -> 1 -> 4 -> 5
Explanation: The first three elements are reversed, and the rest of the list remains unchanged.

EDGE CASE
Input: Head = 1 -> 2 -> 3, k = 5
Output: 3 -> 2 -> 1
Explanation: k exceeds the list's length, so the entire list is reversed.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This is a linked list reversal problem, which often involves modifying node pointers:

- Focus on reversing a specific section of a linked list and reconnecting it properly with the rest of the list.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Reverse the first k nodes of the linked list and connect the reversed section back to the remainder of the list.

```markdown
1) Start with pointers `prev` set to `None` and `current` pointing to `head`.
2) Reverse the next `k` nodes or until the end of the list is reached.
3) Connect the reversed section's end to the next unreversed node.
```

**⚠️ Common Mistakes**

- Not handling the case where k is 0 or the list is empty, which should return the head unchanged.
- Forgetting to reconnect the reversed portion with the rest of the list, which could result in losing part of the list.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def reverse_first_k(head, k):
    if not head or k <= 1:
        return head
    
    current = head
    prev = None
    next_node = None
    count = 0
    
    # Reverse the first k nodes
    while current and count < k:
        next_node = current.next
        current.next = prev
        prev = current
        current = next_node
        count += 1
    
    # Connect the reversed part with the rest of the list
    if head:
        head.next = current
    
    return prev  # New head of the list is the last node of the reversed part
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with an input to check for the expected output
- Catch possible edge cases and off-by-one errors

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(n)` because, in the worst case where `k` is greater than or equal to `n`, the entire list is traversed once.
* **Space Complexity**: `O(1)` because no additional data structures are used; only a few node pointers are needed regardless of the size of the input list.
