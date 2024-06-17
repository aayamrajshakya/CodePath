*[[Unit 6 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 5 mins
* 🛠️ **Topics**: Linked List, Data Structures
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: Can a linked list be empty?
    - A: In this scenario, we are explicitly creating a non-empty list.

```markdown
HAPPY CASE
Input: Assignment statement to create a linked list
Output: 4 -> 3 -> 2
Explanation: Proper creation of the linked list from head to tail with the values 4, 3, and 2 respectively.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

For Linked List construction problems, we want to consider the following approaches:

- Directly initializing the nodes and linking them as specified.
- Utilizing constructor chaining to embed the creation of subsequent nodes within one another.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Construct a linked list by directly linking nodes through a nested constructor pattern.

```markdown
1) Start by creating the last node of the list with a value of 2 and no subsequent node.
2) Create the middle node with a value of 3 and link it to the last node.
3) Create the head node with a value of 4 and link it to the middle node.
```

**⚠️ Common Mistakes**

- Forgetting to correctly set the next reference, resulting in broken links or incorrect list structure.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
Node(4, Node(3, Node(2)))
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with an input to check for the expected output
- Catch possible edge cases and off-by-one errors

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

Assume `N` represents the number of nodes in the linked list.

* **Time Complexity**: `O(1)` because we are simply creating three nodes and linking them, which involves a constant amount of work regardless of input size.
* **Space Complexity**: `O(1)` because the space used does not scale with input size, it remains constant for the three nodes.

