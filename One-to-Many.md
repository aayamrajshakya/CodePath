*[[Unit 6 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 5 mins
* 🛠️ **Topics**: Linked List, Node Construction
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: Are there specific data types or constraints on the node values?
    - A: No, the values can be any type, but here they are strings representing names.

```markdown
HAPPY CASE
Input: Breaking apart the assignment statement as described.
Output: Mario -> Luigi -> Wario
Explanation: The list is correctly assembled from individual nodes connected in sequence.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This is a basic problem of constructing and manually linking a singly linked list node-by-node. It tests basic understanding of node manipulation and pointer assignment.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Create each node independently and then connect them sequentially to form a complete linked list.

```markdown
1) Create the head node 'Mario' with its next initially set to None.
2) Create the 'Luigi' node with its next also set to None.
3) Create the 'Wario' node with its next set to None.
4) Link 'Mario' to 'Luigi' and 'Luigi' to 'Wario' by setting their next properties.
```

**⚠️ Common Mistakes**

- Creating nodes but failing to link them properly, resulting in a broken or incomplete list.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
class Node:
    def __init__(self, value=None, next=None):
        self.value = value
        self.next = next

# Breaking the assignment into multiple lines
head = Node("Mario")
luigi = Node("Luigi")
wario = Node("Wario")
head.next = luigi
luigi.next = wario
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Confirm the link between each node by traversing the list from the head to the tail.
- Ensure that no node is orphaned or incorrectly linked.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(1)` as the operations to create and link nodes involve a constant amount of work.
* **Space Complexity**: `O(1)` in terms of additional space as no extra data structures are used; the space used is proportional to the number of nodes created, which is fixed.

