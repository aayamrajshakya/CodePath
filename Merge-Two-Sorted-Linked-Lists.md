*[[Unit 6 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 30 mins
* 🛠️ **Topics**: Linked Lists, Merging
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: What happens if one of the lists is empty?
  - A: If one list is empty, return the non-empty list as the merged list.

```markdown
HAPPY CASE
Input: List A = 1 -> 2 -> 4, List B = 1 -> 3 -> 4
Output: 1 -> 1 -> 2 -> 3 -> 4 -> 4
Explanation: The nodes are interleaved in sorted order from both lists.

EDGE CASE
Input: List A = 1 -> 2 -> 4, List B = (Empty)
Output: 1 -> 2 -> 4
Explanation: Since List B is empty, the merged list is just List A.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This is a merging problem involving two sorted lists, typically solved by using a temp head to simplify the management of the list's start.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Traverse both lists, comparing and linking nodes in order to form a new sorted list.

```markdown
1) Create a temp node to act as the starting point of the merged list.
2) Compare the current nodes of each list, attach the smaller value to the merged list, and move the pointer in that list forward.
3) Once one list is exhausted, attach the remaining part of the other list.
4) Return the node following the temp, as it represents the start of the merged list.
```

**⚠️ Common Mistakes**

- Forgetting to handle the rest of the list once the other is exhausted.
- Mismanaging the temp head and returning it instead of its next node.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def merge_two_lists(head_a, head_b):
    temp_head = Node(0)
    tail = temp_head
		
    current_a = head_a 
    current_b = head_b 
    while current_a and current_b:
        if current_a.value < current_b.value:
            tail.next = current_a
            current_a = current_a.next
        else:
            tail.next = current_b
            current_b = current_b.next
        tail = tail.next

    # At least one of l1 and l2 can still have nodes 
    # at this point, so connect the remainder
    if current_a:
        tail.next = current_a
    else:
        tail.next = current_b
    
    return temp_head.next
```
 
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Test the function with both lists of varying lengths and contents to ensure proper merging.
- Confirm that the function correctly handles one or both lists being empty.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(n + m)` where `n` and `m` are the lengths of the two lists. Each node is processed once.
* **Space Complexity**: `O(1)` because the merged list is formed by rearranging existing nodes without allocating any new ones.
