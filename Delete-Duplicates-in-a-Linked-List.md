*[[Unit 6 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 25 mins
* 🛠️ **Topics**: Linked Lists, Removing Duplicates
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: What if all elements are duplicates?
  - A: The list should end up empty except for the temp head.

```markdown
HAPPY CASE
Input: 1 -> 2 -> 2 -> 3 -> 3
Output: 1
Explanation: Duplicates of 2 and 3 are removed, leaving only 1.

EDGE CASE
Input: 1 -> 1 -> 1
Output: (Empty)
Explanation: All nodes are duplicates and are thus removed.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem involves removing duplicates from a sorted linked list, which is typically tackled using a pointer to track the last unique node and another to skip duplicates.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use a temp node to handle edge cases easily, and two pointers to manage duplicates.

```markdown
1) Initialize a temp node with next pointing to head.
2) Use two pointers: one to keep track of the last node before a series of duplicates (prev) and another to traverse and skip duplicates (current).
3) Adjust links to skip over duplicates.
4) Return the modified list starting from temp's next.
```

**⚠️ Common Mistakes**

- Failing to properly reconnect the non-duplicate part of the list after skipping duplicates.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def delete_dupes(head):
    # Use a temp node to simplify head operations
    temp = Node(0)
    temp.next = head

    # `prev` is the last node before the current sequence of duplicates or unique values
    prev = temp
    current = head

    while current:
        # Move current to skip over all duplicates
        while current.next and current.value == current.next.value:
            current = current.next

        # If `prev.next` is `current`, no duplicates were found between `prev` and `current`
        if prev.next == current:
            prev = prev.next
        else:
            # Otherwise, skip all duplicates
            prev.next = current.next

        # Move current to the next distinct value
        current = current.next

    return temp.next
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Test the function with a list having multiple duplicates to see if they are removed properly.
- Use an edge case with all identical elements to ensure the list is emptied appropriately.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(N)` where `N` is the number of nodes in the list. Each node is processed once.
* **Space Complexity**: `O(1)` since no extra space is used beyond a few pointers for management.
