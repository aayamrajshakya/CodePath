*[[Unit 6 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 25 mins
* 🛠️ **Topics**: Doubly Linked Lists, Rotations
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: How is the list behavior affected if `k` is zero or a multiple of the list length?
  - A: The list remains unchanged as the rotation brings it back to its original state.

```markdown
HAPPY CASE
Input: 1 <-> 2 <-> 3 <-> 4 <-> 5, k = 2
Output: 4 <-> 5 <-> 1 <-> 2 <-> 3
Explanation: The list is rotated left by 2 places, changing the head.

EDGE CASE
Input: 1 <-> 2 <-> 3 <-> 4 <-> 5, k = 5
Output: 1 <-> 2 <-> 3 <-> 4 <-> 5
Explanation: Rotating by the list's length results in no visible change.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem is a rotation of a doubly linked list, which involves adjusting the head after determining the new head based on `k`.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Find the new head after `k` rotations, adjust the previous and next pointers accordingly to maintain the doubly linked list structure.

```markdown
1) Count the length of the list and determine the effective rotations (`k % length`).
2) Identify the new head after the effective rotations.
3) Adjust the previous head's previous pointer to point to the last node.
4) Set the new head's previous pointer to null and adjust the old tail's next pointer to the original head.
5) Return the new head as the start of the rotated list.
```

**⚠️ Common Mistakes**

- Not properly reconnecting the next and previous pointers in the new head and tail, potentially breaking the doubly linked structure.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def rotate_doubly_linked_list(head, k):
    if not head or k == 0:
        return head
    
    # Find the length and the last node
    last = head
    length = 1
    while last.next:
        last = last.next
        length += 1
    
    # Effective rotations
    k = k % length
    if k == 0:
        return head
    
    # New tail is the current head after k rotations to the left
    new_tail = head
    for _ in range(k - 1):
        new_tail = new_tail.next
    
    new_head = new_tail.next
    
    # Adjust the connections
    last.next = head
    head.prev = last
    new_tail.next = None
    new_head.prev = None
    
    return new_head
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Test the rotation with various values of k, especially those larger than the list length and those that result in no change (multiples of the length).

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(n)` where `n` is the length of the list to find the tail and calculate the length.
* **Space Complexity**: `O(1)` as no extra space is needed beyond a few pointers for manipulation.
