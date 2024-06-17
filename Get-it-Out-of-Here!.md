*[[Unit 6 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 15 mins
* 🛠️ **Topics**: Linked Lists, Debugging
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: What if the value to be removed appears more than once?
    - A: The function should only remove the first occurrence of the value.

```markdown
HAPPY CASE
Input: Head = 1 -> 2 -> 3 -> 4, Value to remove = 2
Output: 1 -> 3 -> 4
Explanation: The node with value 2 is removed as expected.

EDGE CASE
Input: Head = 1 -> 1 -> 1 -> 4, Value to remove = 1
Output: 1 -> 1 -> 4
Explanation: Only the first occurrence of 1 is removed.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem is a variant of linked list manipulation specifically focused on node deletion:

- Commonly involves checking and updating node references.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Identify where to put print statements to debug the function effectively.

```markdown
1) Add a print statement at the beginning to print the initial list.
2) Add print statements before and after any conditional or value-changing operation to trace changes.
3) Include a print statement inside the loop to monitor the current and next node values.
4) Fix the bug by updating the removal logic when a match is detected.
```
**⚠️ Common Mistakes**

- Not handling the case where the value to be removed is at the head or the tail of the list.
- Incorrect pointer updates that could lead to losing track of the rest of the list.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
# Possible print statements
def remove_by_value(head, val):
    if not head:
        return None
    if head.value == val:
        return head.next  

    current = head
    while current.next:
	# print(f"Current: {current.next.value}")
	# print(f"Current Next: {current.next.value}")
        if current.next.value == val:
            current.next = current.next.next  # FIX: change from incorrect "current = current.next.next"
            # print(f"New Current Next: {current.next}")
            return head  
        current = current.next
    return head
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Validate the function with several inputs to ensure it handles different cases correctly.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(n)` because we may need to traverse the entire list.
* **Space Complexity**: `O(1)` as no extra space is used aside from temporary pointers.


