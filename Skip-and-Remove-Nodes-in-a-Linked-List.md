*[[Unit 6 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 30 mins
* 🛠️ **Topics**: Linked Lists, List Manipulation
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: What if the total nodes are fewer than `m`?
  - A: The list should not change as there will be no `n` nodes to remove after skipping `m` nodes.

```markdown
HAPPY CASE
Input: 1 -> 2 -> 3 -> 4 -> 5 -> 6, m = 2, n = 2
Output: 1 -> 2 -> 5 -> 6
Explanation: First 2 nodes are kept, next 2 nodes are removed, and the remaining nodes are kept.

EDGE CASE
Input: 1 -> 2 -> 3, m = 4, n = 1
Output: 1 -> 2 -> 3
Explanation: As `m` is larger than the total number of nodes, no nodes are deleted.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem involves modifying a linked list by skipping certain nodes and removing others, using pointer manipulation without extra space.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Traverse the list, skip `m` nodes, then remove `n` nodes. Repeat the pattern until the end of the list.

```markdown
1) Use a pointer to traverse the list.
2) Skip `m` nodes, ensuring the pointer does not reach the end of the list prematurely.
3) Remove `n` nodes, adjusting pointers to bypass them.
4) Repeat until the end of the list is reached.
5) Return the head of the modified list.
```

**⚠️ Common Mistakes**

- Incorrectly counting nodes during the skip and remove phases.
- Failing to handle cases where `m` or `n` exceeds the number of remaining nodes.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def skip_and_remove(head, m, n):
    current = head
    while current:
        # Skip m nodes
        for i in range(1, m):
            if current is None:
                return head
            current = current.next

        # Now current is the last node before the n nodes to delete
        if current is None:
            return head

        # Start deletion of next n nodes
        temp = current
        for j in range(n):
            if temp.next is None:
                break
            temp = temp.next

        # Connect the current node to the node after the N deleted nodes
        if current and temp.next:
            current.next = temp.next
        current = temp.next

    return head
```
    
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Test with multiple configurations of `m` and `n` to ensure nodes are correctly skipped and removed.
- Validate with lists shorter than `m` to see that no changes are made.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(n)` where `n` is the total number of nodes in the list. Each node is processed up to once.
* **Space Complexity**: `O(1)` because no additional space is used; modifications are done in-place.
