*[[Unit 6 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 30 mins
* 🛠️ **Topics**: Linked Lists, Aggregation
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: What happens to zeros in the list?
  - A: Zeros are not included in the sum and are only used as separators between sequences to be summed.

```markdown
HAPPY CASE
Input: 0 -> 1 -> 2 -> 3 -> 0 -> 4 -> 5 -> 0
Output: 6 -> 9
Explanation: Sums between zeros are calculated and listed (1+2+3=6 and 4+5=9).

EDGE CASE
Input: 0 -> 0 -> 1 -> 0
Output: 1
Explanation: Only one non-zero value between zeros, directly copied to the result.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem involves traversing a linked list and performing aggregation based on separators (zeros), a kind of run-length encoding in reverse.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Traverse the list, summing values between zeros and adding each sum to a new list upon reaching the next zero.

```markdown
1) Initialize a temp head for the result list and a pointer to manage the current sum.
2) Traverse the original list, adding values to the current sum until a zero is encountered.
3) Upon hitting a zero, if a sum has been accumulated, append it to the result list and reset the sum.
4) Continue until the end of the list is reached.
5) Return the list starting after the temp head.
```

**⚠️ Common Mistakes**

- Including zero values in sums.
- Failing to handle consecutive zeros by skipping the creation of a sum node.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def merge_nodes(head):
    temp = Node(0)  # Temp node to handle edge cases cleanly
    current_sum = 0
    new_list_tail = temp  # Tail of the new linked list

    current = head.next  # Start from the first node after the initial zero
    while current:
        if current.value == 0:
            if current_sum > 0:  # Only add a node if the sum is non-zero
                new_list_tail.next = Node(current_sum)
                new_list_tail = new_list_tail.next
            current_sum = 0  # Reset sum after reaching a zero
        else:
            current_sum += current.value  # Accumulate values between zeros
        
        current = current.next  # Move to the next node

    return temp.next  # The first node after the temp node is the head of the result list
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Test with lists having various patterns of zeros and numbers to ensure correct summation and node creation.
- Validate cases with multiple consecutive zeros to confirm no erroneous nodes are created.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(n)` where `n` is the number of elements in the original list, as each element is processed once.
* **Space Complexity**: `O(m)` where `m` is the number of non-zero segments in the list, determining the number of new nodes created.
