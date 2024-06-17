*[[Unit 6 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 30 mins
* 🛠️ **Topics**: Linked Lists, Reverse Operations
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: What happens if `m` and `n` are the same?
  - A: No change is made to the list since the range to reverse is only one node.

```markdown
HAPPY CASE
Input: 1 -> 2 -> 3 -> 4 -> 5, m = 2, n = 4
Output: 1 -> 4 -> 3 -> 2 -> 5
Explanation: Nodes between position 2 and 4 are reversed, leading to the sequence 4 -> 3 -> 2.

EDGE CASE
Input: 1 -> 2 -> 3, m = 1, n = 1
Output: 1 -> 2 -> 3
Explanation: As m and n are the same, no nodes are reversed, and the list remains unchanged.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem is a variation of the classic linked list reversal but with a constraint to only reverse a subsection of the list.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use a temporary node to simplify edge cases and use pointers to reverse the specified section.

```markdown
1) Create a temp node to simplify operations at the head.
2) Use pointers to navigate to the start of the section to reverse.
3) Reverse the nodes between m and n using pointer manipulation.
4) Connect the reversed section back into the list.
```

**⚠️ Common Mistakes**

- Failing to reconnect the reversed section properly with the rest of the list.
- Not handling the case where the reverse starts from the head node.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def reverse_between(head, m, n):
    if not head or m == n:
        return head

    # Create a temporary head node to simplify edge cases where m is 1
    temp_head = Node(0)
    temp_head.next = head
    prev = temp_head

    # Step 1: Reach the node just before position m
    for i in range(m - 1):
        prev = prev.next
    
    # `prev` now is the node just before m, and `start` will be the first node to reverse
    start = prev.next
    then = start.next

    # Step 2: Reverse from m to n
    for _ in range(n - m):
        start.next = then.next  # Remove `then` from the list
        then.next = prev.next  # Insert `then` at the beginning of the reversed section
        prev.next = then  # Move `prev` to point to `then` as the new start of the reversed section
        then = start.next  # Move `then` to the next node to be reversed

    return temp_head.next
```
    
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Run through the code with a typical example to ensure that the section is reversed and properly linked.
- Check with the edge case where m and n are the same to confirm no unnecessary changes are made.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(N)` since we might need to traverse the entire list in the worst case.
* **Space Complexity**: `O(1)` as we are using a constant amount of space regardless of the input size.
