*Originally from [[Unit 6 Session 2]] (Click for link to problem statements)*

*Reviewed in [[Unit 10 Session 2]]*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 20 mins
* 🛠️ **Topics**: Linked Lists, Arithmetic Operations
* 📺 **Non-TIP101 Version**: [[Add Two Numbers]]

## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: What if one of the lists is longer than the other?
  - A: Continue to process the longer list after the shorter one has been fully traversed.

```markdown
HAPPY CASE
Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)
Output: 7 -> 0 -> 8
Explanation: 342 + 465 = 807, so the list is 7 -> 0 -> 8.

EDGE CASE
Input: (0) + (0)
Output: 0
Explanation: 0 + 0 = 0, no carry is involved and only one node is needed.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This is a problem involving arithmetic operations directly on linked lists, typically solved using a carry variable and direct digit-wise addition.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Simultaneously traverse both linked lists, adding corresponding digits along with any carry, and form a new linked list with the sum.

```markdown
1) Initialize a temp node to handle the result and a pointer for the current node in the result list.
2) Traverse both lists, adding values of corresponding nodes plus any carry.
3) Store the units digit in the current node of the result list and update the carry.
4) Continue until both lists are exhausted and any carry is added.
5) Ensure to handle any remaining nodes from the longer list.
```

**⚠️ Common Mistakes**

- Forgetting to handle the carry once the shorter list is exhausted.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def add_two_numbers(head_a, head_b):
    # Temp head to simplify handling the result list
    temp_head = Node()
    current = temp_head
    carry = 0
    
    a_current = head_a
    b_current = head_b
    while a_current or b_current or carry:
        val_a = a_current.value if a_current else 0
        val_b = b_current.value if b_current else 0

        # Calculate the sum of values and the carry
        sum_val = val_a + val_b + carry
        carry = sum_val // 10
        sum_val = sum_val % 10

        # Append the result to the new list
        current.next = Node(sum_val)
        current = current.next

        # Move to the next elements in the lists
        if a_current:
            a_current = a_current.next
        if b_current:
            b_current = b_current.next

    return temp_head.next
```
    
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Test with inputs where one list is longer than the other to ensure correct handling of carry over.
- Verify edge cases like both lists containing only zeros.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(max(m, n))` where `m` and `n` are the lengths of the two lists, since each node in both lists needs to be processed.
* **Space Complexity**: `O(max(m, n))` for the new list that might be as long as the longer of the two input lists plus one more node for a possible carry.
