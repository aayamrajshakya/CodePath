*[[Unit 6 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 10 mins
* 🛠️ **Topics**: Linked Lists, Binary Representation
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: What if the linked list is empty?
  - A: Return 0 as there are no binary digits to convert.

```markdown
HAPPY CASE
Input: 1 -> 0 -> 1 -> 1
Output: 11
Explanation: The linked list represents the binary number 1011, which equals 11 in decimal.

EDGE CASE
Input: 0
Output: 0
Explanation: The linked list represents the binary number 0, which equals 0 in decimal.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This is a typical problem involving the conversion of a binary number stored in a linked list to its decimal equivalent.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Traverse the linked list while building the binary number and convert it to its decimal form.

```markdown
1) Initialize a variable to keep track of the number.
2) Traverse the linked list from the head.
3) For each node, multiply the current number by 2 (left shift in binary) and add the node's value.
4) Return the final number.
```

**⚠️ Common Mistakes**

- Not considering an empty list, which should return 0.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def binary_to_int(head):
    num = 0
    current = head
    while current:
        # Multiply the current number by 2 
        # and add the current node's value to it
        num = num * 2 + current.value
        current = current.next
    return num
```
    
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Use the happy case to check for correct binary to decimal conversion.
- Use the edge case of a single node with 0 to ensure it returns 0.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(n)` where `n` is the number of nodes in the linked list, as each node is processed once.
* **Space Complexity**: `O(1)` because no additional space is required beyond a variable to accumulate the decimal value.
