*[[Unit 6 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 20 mins
* 🛠️ **Topics**: Linked Lists, Rotations
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: What happens if k is greater than the length of the list?
  - A: Since we'll temporarily make the list circular, k should be taken modulo the length of the list to find the effective number of rotations.

```markdown
HAPPY CASE
Input: 1 -> 2 -> 3 -> 4 -> 5, k = 2
Output: 4 -> 5 -> 1 -> 2 -> 3
Explanation: The list is rotated to the right by 2 places.

EDGE CASE
Input: 1 -> 2 -> 3 -> 4 -> 5, k = 5 (or 0)
Output: 1 -> 2 -> 3 -> 4 -> 5
Explanation: Rotating by the list's length results in the same list.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem involves rotating a list, which is typically tackled by linking the list into a circle, then adjusting the links based on k.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Connect the list into a circular form, then adjust the head and tail based on the rotation count k.

```markdown
1) Measure the length of the list and identify the last node.
2) Link the last node to the head to form a circular list.
3) Calculate the effective rotation using k modulo the length of the list.
4) Find the new tail (length - k % length steps from the head).
5) Make the node following the new tail the new head and break the circle there.
```

**⚠️ Common Mistakes**

- Not adjusting for k values greater than the list length.
- Not handling edge cases where the list does not change (k is 0 or a multiple of the list length).

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def rotate_right(head, k):
    if not head or not head.next or k == 0:
        return head

    last = head
    length = 1
    while last.next:
        last = last.next
        length += 1

    last.next = head

    steps_to_new_tail = length - k % length
    new_tail = head
    for _ in range(steps_to_new_tail - 1):
        new_tail = new_tail.next

    new_head = new_tail.next
    new_tail.next = None

    return new_head
```
  
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Test the rotation with values of k that are less than, equal to, and greater than the list length to ensure proper rotation.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(n)` where `n` is the length of the list, as the list is traversed completely to find the length and to adjust the tail.
* **Space Complexity**: `O(1)` because no additional storage is used; the list nodes are just re-linked.
