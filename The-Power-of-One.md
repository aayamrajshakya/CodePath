*[[Unit 6 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 5 mins
* 🛠️ **Topics**: Linked List, Data Structures, Code Refactoring
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Have fully understood the problem and have no clarifying questions.

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.


This task involves creating a linked list in a more compact and efficient manner than originally provided, showcasing how constructor chaining can be used to streamline the code.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Instead of manually linking each node line by line, use constructor nesting to directly link all nodes in a single statement.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
head = Node("Ash", Node("Misty", Node("Brock")))
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- The new implementation should create a linked list starting at "Ash" and ending at "Brock" without any intermediary steps or additional assignments.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

- **Time Complexity:** The constructor for each node is called once, resulting in constant time operations for each node creation. The overall time complexity for creating the linked list is `O(1)` as the operations do not depend on the length of the list or scale with more data.
- **Space Complexity:** Each node creation uses a constant amount of space. The total space used is proportional to the number of nodes, which in this fixed example, remains constant (`O(1)`).