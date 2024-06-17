*[[Unit 10 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 30 mins
* 🛠️ **Topics**: Linked List, Two Pointers
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- What should be returned if both lists are empty?
    - None, since both lists are empty.
- What should be returned if one of the lists is empty?
    - The non-empty list should be returned as the merged list.

```
HAPPY CASE
Input: head_a = 1 -> 3 -> 5, head_b = 2 -> 4 -> 6
Output: 1 -> 2 -> 3 -> 4 -> 5 -> 6
Explanation: Nodes are taken alternately from each list.

HAPPY CASE
Input: head_a = 1 -> 3, head_b = 2 -> 4 -> 6
Output: 1 -> 2 -> 3 -> 4 -> 6
Explanation: Remaining nodes from head_b are appended at the end.

EDGE CASE
Input: head_a = None, head_b = 1 -> 2 -> 3
Output: 1 -> 2 -> 3
Explanation: Since head_a is empty, the merged list is just head_b.

EDGE CASE
Input: head_a = None, head_b = None
Output: None
Explanation: Both lists are empty, so the merged list is also empty.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

For Linked List problems, we want to consider the following approaches:

- Using two pointers to traverse both lists simultaneously.
- Alternating nodes from each list to build the merged list.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Traverse both lists with two pointers, alternately appending nodes to the merged list. If one list is exhausted, append the remaining nodes from the other list.

```
1) Check if either head_a or head_b is None, return the non-None list.
2) Initialize merged_head with head_a and set current pointers for both lists.
3) Use a toggle to alternate between the lists while traversing.
4) Append nodes alternately from each list to the merged list.
5) If one list is exhausted, append the remaining nodes from the other list.
6) Return the merged_head.
```

**⚠️ Common Mistakes**

- Forgetting to handle cases where one or both lists are empty.
- Incorrectly switching between lists during alternation.
- Not properly updating the pointers.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```
def shuffle_merge(head_a, head_b):
    if not head_a:
        return head_b
    if not head_b:
        return head_a
    
    # Initialize the merged list with the first node of list A
    merged_head = head_a
    current_a = head_a.next
    current_b = head_b
    current_merged = merged_head

    # Alternate appending nodes from each list
    toggle = True  # Starts with List B because List A's head is already used
    while current_a and current_b:
        if toggle:
            current_merged.next = current_b
            current_b = current_b.next
        else:
            current_merged.next = current_a
            current_a = current_a.next
        current_merged = current_merged.next
        toggle = not toggle  # Switch between List A and List B

    # Append the remaining nodes from either list
    current_merged.next = current_a if current_a else current_b

    return merged_head
```
 
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with an input to check for the expected output.
- Example: Trace with head_a = 1 -> 3 -> 5, head_b = 2 -> 4 -> 6
    - merged_head = 1
    - Toggle to List B, append 2
    - Toggle to List A, append 3
    - Toggle to List B, append 4
    - Toggle to List A, append 5
    - List A is exhausted, append remaining nodes from List B

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

Assume `N` and `M` represent the lengths of the linked lists `head_a` and `head_b` respectively.

* **Time Complexity**: `O(N + M)` because we need to traverse all nodes in both lists.
* **Space Complexity**: `O(1)` because we only use a constant amount of extra space.