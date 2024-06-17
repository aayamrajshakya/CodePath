*[[Unit 6 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 25 mins
* 🛠️ **Topics**: Linked Lists, Partitioning
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: What if the linked list is empty?
  - A: Return None as there are no nodes to partition.

```markdown
HAPPY CASE
Input: List = 3 -> 5 -> 8 -> 5 -> 10 -> 2 -> 1, val = 5
Output: 3 -> 2 -> 1 -> 5 -> 8 -> 5 -> 10
Explanation: All nodes with values less than 5 come before nodes with values 5 or greater.

EDGE CASE
Input: List = 2 -> 1 -> 3, val = 4
Output: 2 -> 1 -> 3
Explanation: All node values are less than 4, so the list remains unchanged.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

For partitioning problems, consider strategies such as the two-pointer technique where one pointer builds the "less than" list and another builds the "greater than or equal to" list.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Create two separate linked lists for elements less than and greater than the partition value, then combine them.

```markdown
1) Initialize two new linked list heads: one for elements less than 'val' and one for elements greater or equal.
2) Traverse through the original list, appending elements to the appropriate new list.
3) Finally, merge the two lists by connecting the tail of the 'less' list to the head of the 'greater' list.
4) Ensure the 'greater' list ends with a null to avoid cycles.
```

**⚠️ Common Mistakes**

- Not ending the greater list with a null, leading to potential cycles.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def partition(head, val):
    # Create two temp heads to start the less and greater lists
    less_head = Node(0)
    greater_head = Node(0)
    
    # These pointers will be used to add nodes to the less and greater lists
    less = less_head
    greater = greater_head
    
    # Traverse the original list
    current = head
    while current:
        if current.val < val:
            less.next = current
            less = less.next
        else:
            greater.next = current
            greater = greater.next
        
        current = current.next
    
    # Important: end the greater list to prevent cycles
    greater.next = None
    
    # Attach the end of the less list to the start of the greater list
    # Important: Skip the temp head
    less.next = greater_head.next
    
    return less_head.next
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Test with the happy case to ensure proper partitioning.
- Test with an edge case where all elements are less than the partition value to confirm no change in list structure.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(N)` because we need to traverse the list once.
* **Space Complexity**: `O(1)` because we only use existing nodes without allocating new space except for the two temp head nodes.
