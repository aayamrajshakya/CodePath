*[[Unit 6 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 10 mins
* 🛠️ **Topics**: Linked List, Debugging

## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: How should the function behave when attempting to remove a node not present in the list?
    - A: The function should traverse the entire list and return the unchanged list.

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g., Linked List or Dynamic Programming, and strategies or patterns in those categories.

This debugging task involves tracing through a linked list deletion operation to ensure that all nodes can potentially be removed, including the last node.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use print statements to trace the path taken by the pointers, especially near the end of the list, to understand why the last node isn't being removed when it matches the given value.

```markdown
1) Insert a print statement at the start to check if the list is empty.
2) Insert a print statement when checking if the head node is the node to be removed.
3) Add print statements within the loop to:
   - Print the current node's value and the next node's value (if any).
   - Print a message before the conditional that checks for the node to remove.
4) Add a print statement at the end if no matching node is found.
5) Fix the bug by modifying the loop condition to ensure the last node is also checked.
```

## 4: I-mplement

> **Implement** the code to solve the algorithm with added print statements for debugging.

```python
# Possible print statements
def remove_by_value(head, val):
    if head is None:
        return head

    # If the node to be removed is the head of the list
    if head.value == val:
        return head.next

    # Initialize pointers
    current = head.next
    previous = head

    while current: # FIXED: Changed from current.next to current
        print(f"Next: {current.next}") # Should show that we don't iterate over last node in list
        if current.value == val:
            previous.next = current.next
            return head
        previous = current
        current = current.next

    return head


# Possible test cases
head = Node(1, Node(2, Node(3, Node(4))))
new_head = remove_by_value(head, 3)
print_list(new_head)  # Expected: 1 -> 2 -> 4

head = Node(1, Node(2, Node(3, Node(4))))
new_head = remove_by_value(head, 4)
print_list(new_head)  # Expected: 1 -> 2 -> 3 
# Actual will be: 1 -> 2 -> 3 -> 4
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Use the provided test cases to observe the output and behavior of the list when nodes are removed.
- Ensure that the last node can now be removed.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(n)` where `n` is the number of nodes in the linked list. The function potentially iterates through each node once.
* **Space Complexity**: `O(1)` because only a few pointers are used, and no additional data structures are created.

