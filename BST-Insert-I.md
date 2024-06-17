*[[Unit 8 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 15 mins
* 🛠️ **Topics**: Trees, Binary Search Trees, Data Insertion
    
## 1: U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Question: What should happen if a key already exists in the tree?
    - Answer: Update the existing node's value instead of adding a new node.

```
HAPPY CASE
Input: TreeNode(10, TreeNode(5), TreeNode(15)), key = 7, value = "new"
Output: TreeNode structure including new TreeNode(7) under TreeNode(5).
Explanation: Node 7 does not exist, it is inserted in the correct position to maintain BST properties.

EDGE CASE
Input: TreeNode(10, TreeNode(5), TreeNode(15)), key = 5, value = "updated"
Output: TreeNode(10, TreeNode(5, value="updated"), TreeNode(15))
Explanation: Key 5 exists, so its value is updated instead of inserting a new node.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem is a classic example of inserting or updating nodes in a binary search tree, crucial for maintaining sorted data structures efficiently.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Traverse the tree according to BST rules (left for less, right for more) to find the correct position for the new node or update an existing one.

```
1) If the tree is empty, insert the new node as the root.
2) If the key of the current node is greater than the new key, recurse left.
3) If the key of the current node is less than the new key, recurse right.
4) If the key matches, update the node’s value.
```

**⚠️ Common Mistakes**

- Not updating the value of an existing node and adding a duplicate node instead.
- Failing to maintain the BST properties during insertion.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def insert(root, key, value):
    """
    Insert a new node with the given `key` and `value` into the binary search tree rooted at `root`.
    Return the root of the modified tree.
    """
    if root is None:
        return TreeNode(key, value)

    if key < root.val:
        root.left = insert(root.left, key, value)
    elif key > root.val:
        root.right = insert(root.right, key, value)
    else:
        # Key exists, update the node's value
        root.val = value

    return root
```
    
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Use a range of keys and values to ensure the tree correctly handles both insertion and updates, and retains its BST properties.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: `O(h)` where h is the height of the tree, potentially `O(log n)` in a balanced BST but could degrade to `O(n)` if the tree becomes skewed.
* **Space Complexity**: `O(h)` due to recursion depth, which may also degrade depending on the tree’s balance.
