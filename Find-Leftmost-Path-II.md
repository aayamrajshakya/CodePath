*[[Unit 8 Session 1]] (Click for link to problem statements)*

*Looking for the recursive version of this problem?  Go to [[Find Leftmost Path I]]*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 10 mins
* 🛠️ **Topics**: Trees, Binary Trees, Iterative Algorithms
    
## 1: U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Question: What should the function return if the tree is empty?
    - Answer: The function should return an empty list as there is no path to traverse.

```
HAPPY CASE
Input: TreeNode('a', TreeNode('b', TreeNode('d'), None), None)
Output: ['a', 'b', 'd']
Explanation: The leftmost path from the root 'a' leads to 'b' and continues to 'd', found iteratively.

EDGE CASE
Input: TreeNode('a')
Output: ['a']
Explanation: The tree has only one node, so the leftmost path includes just the root node.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem is categorized under tree traversal, particularly focusing on an iterative approach to find a path. It aligns with strategies used in non-recursive tree navigation, akin to using a stack but simplified for a direct left descent.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Traverse the tree from the root, moving always to the left child until no more children are available.

```
1) Start with the root node.
2) While a current node exists, add its value to the path list.
3) Move to the left child of the current node.
4) Return the path list once the leftmost child is reached or when a leaf is encountered.
```

**⚠️ Common Mistakes**

- Forgetting to handle the null root case, leading to attempts to access properties of None.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def left_path(root):
    """
    Prints the leftmost path of the binary tree rooted at `root`.
    """
    current = root
    path = []
    while current is not None:
        path.append(current.val)
        current = current.left
    return path
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Conduct tests with a variety of tree shapes to confirm that the path correctly identifies the leftmost nodes from root to leaf.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(n)` in the worst case where n is the height of the tree, specifically when the tree is skewed to the left. This assumes a worst-case scenario where each node has only a left child.
* **Space Complexity**: `O(1)` since no additional data structures are used beyond the list to store the path.
