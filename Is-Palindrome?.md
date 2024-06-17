*[[Unit 6 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 20 mins
* 🛠️ **Topics**: Linked List, Two Pointers, Palindrome Checking
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: What should the function return for a list with mixed data types, like integers and characters?
    - A: The function assumes all nodes in the linked list are of the same data type and are comparable.

```markdown
HAPPY CASE
Input: head = Node('a', Node('b', Node('b', Node('a'))))
Output: True
Explanation: The linked list represents the string 'abba', which is a palindrome.

EDGE CASE
Input: head = Node('a')
Output: True
Explanation: A single character is inherently a palindrome since it reads the same forward and backward.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

The problem is a typical example of palindrome checking in data structures, effectively handled using the two-pointer technique.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use the two-pointer technique to identify the middle of the list, reverse the second half, and then compare the first half to the reversed second half.

```markdown
1) Use two pointers (slow and fast) to find the middle of the list. Move slow by one step and fast by two steps until fast reaches the end.
2) Reverse the second half of the list starting from the slow pointer.
3) Compare the first half with the reversed second half. If any values do not match, return False.
4) Return True if all corresponding values match.
```

**⚠️ Common Mistakes**

- Not handling edge cases like empty lists or single-element lists.
- Errors in reversing the second half of the list.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
class Node:
    def __init__(self, value=None, next=None):
        self.value = value
        self.next = next

def is_palindrome(head):
    if head is None or head.next is None:
        return True  # A list with 0 or 1 element is a palindrome

    # Find the middle of the list
    slow = fast = head
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
    
    # Reverse the second half of the list
    prev = None
    while slow:
        next_node = slow.next
        slow.next = prev
        prev = slow
        slow = next_node
    
    # Compare the first half and the reversed second half
    left, right = head, prev
    while right:  # Only need to compare till the end of the second half
        if left.value != right.value:
            return False
        left = left.next
        right = right.next
    
    return True
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Confirm that it correctly identifies palindromes in various configurations and sizes.
- Ensure that reversing the second half and comparisons are correctly implemented.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(n)` where `n` is the length of the linked list. The list is traversed multiple times: once to find the middle, once to reverse the second half, and once more to compare the halves.
* **Space Complexity**: `O(1)` as no additional data structures of variable length are created; only a fixed number of node pointers are used regardless of the list size.

