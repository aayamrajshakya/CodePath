*[[Unit 10 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 30 mins
* 🛠️ **Topics**: Tree, Depth-First Search (DFS)

## 1: U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- What should be returned if the tree is empty?
    - An empty list `[]`, since there are no nodes to collect.

```
HAPPY CASE
Input: root = [1, 2, 3, 4, 5]
Output: [[4, 5, 3], [2], [1]]
Explanation: First collect [4, 5, 3], then [2], and finally [1].

HAPPY CASE
Input: root = [1]
Output: [[1]]
Explanation: Only one node, so only one collection step.

EDGE CASE
Input: root = []
Output: []
Explanation: The tree is empty, so the output is an empty list.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

For Tree problems, we want to consider the following approaches:

- Using Depth-First Search (DFS) to collect and remove leaf nodes recursively.
- Modifying the tree structure in place to remove the leaves.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use a helper function to recursively remove the leaf nodes and collect their values. Repeat this process until the tree is empty.

```
1) Define a helper function `remove_leaves(node)` that:
    a) Returns None if the node is None.
    b) If the node is a leaf (both left and right children are None), append its value to a list `leaves` and return None.
    c) Recursively call `remove_leaves` on the left and right children.
    d) Update the node's left and right children with the results of the recursive calls.
    e) Return the node.
2) Initialize an empty list `result` to store the collections of leaves.
3) While the root is not None:
    a) Initialize an empty list `leaves` to collect the current set of leaves.
    b) Call `remove_leaves` with the root.
    c) Append the list `leaves` to `result`.
4) Return `result`.
```

**⚠️ Common Mistakes**

- Not correctly handling the case where the tree is empty.
- Incorrectly updating the tree structure when removing leaves.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```
def find_leaves(root):
    result = []

    def remove_leaves(node):
        if not node:
            return None
        if not node.left and not node.right:
            leaves.append(node.val)
            return None
        node.left = remove_leaves(node.left)
        node.right = remove_leaves(node.right)
        return node

    while root:
        leaves = []
        root = remove_leaves(root)
        result.append(leaves)

    return result
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with an input to check for the expected output.
- Example: Trace with `root = [1, 2, 3, 4, 5]`
    - Collect `[4, 5, 3]`, then `[2]`, and finally `[1]`
    - Result: `[[4, 5, 3], [2], [1]]`

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

Assume `N` represents the number of nodes in the tree.

* **Time Complexity**: `O(N^2)` in the worst case where the tree is skewed because each call to remove_leaves traverses the entire height of the tree.
* **Space Complexity**: `O(N)` due to the space required to store the result and the recursion stack.