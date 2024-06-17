*[[Unit 8 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 5 mins
* 🛠️ **Topics**: Trees, Binary Trees
    
## 1: U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

For tree construction problems, we typically need to:
- Understand the TreeNode structure.
- Assign values and children to nodes correctly to build the desired structure.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Create nodes for each value and connect them as per the given tree structure.

```
1) Create a TreeNode with value 10.
2) Create a TreeNode with value 4 and assign it to the left of the root node.
3) Create a TreeNode with value 6 and assign it to the right of the root node.
```

**⚠️ Common Mistakes**

- Not properly linking children to their respective parents which could lead to a tree that does not reflect the given structure.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
root = TreeNode(10)
root.left = TreeNode(4)
root.right = TreeNode(6)
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with the created tree to ensure that each node is connected correctly according to the problem statement.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(1)` because we are just instantiating three nodes and linking them, which involves a constant amount of work.
* **Space Complexity**: `O(1)` because the total space used does not scale with input size; it is constant regardless of scenario.
