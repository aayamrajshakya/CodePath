*[[Unit 10 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 25 mins
* 🛠️ **Topics**: Tree, Recursion
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- What should be returned if the tree is empty?
    - True, since an empty tree satisfies the condition trivially.

```
HAPPY CASE
Input: root = [10, 4, 6]
Output: True
Explanation: The root's value (10) equals the sum of its descendants (4 + 6).

HAPPY CASE
Input: root = [5, 3, 1]
Output: False
Explanation: The root's value (5) does not equal the sum of its descendants (3 + 1).

EDGE CASE
Input: root = []
Output: True
Explanation: An empty tree trivially satisfies the condition.

EDGE CASE
Input: root = [0]
Output: True
Explanation: The tree has only one node, so it satisfies the condition.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

For Tree problems, we want to consider the following approaches:

- Using recursion to traverse the tree and calculate the sum of all descendant nodes.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use a helper function to calculate the sum of all nodes in the tree. Then, compare the root's value with the sum of its left and right subtrees.

```
1) Define a helper function `sum_of_subtrees(node)` that:
    a) Returns 0 if the node is None.
    b) Returns the sum of the node's value and the sums of its left and right subtrees.
2) Define the main function `check_root_sum(root)` that:
    a) Returns True if the root is None (an empty tree).
    b) Calculates the sum of the left and right subtrees.
    c) Compares the root's value with the sum of the left and right subtrees.
    d) Returns True if they are equal, otherwise False.
```

**⚠️ Common Mistakes**

- Forgetting to handle the case where the tree is empty.
- Not correctly summing the values of all descendant nodes.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```
def sum_of_subtrees(root):
    if not root:
        return 0
    return root.val + sum_of_subtrees(root.left) + sum_of_subtrees(root.right)

def check_root_sum(root):
    if not root:
        return True  # An empty tree satisfies the condition trivially

    # Get the sum of the left and right subtrees
    left_sum = sum_of_subtrees(root.left)
    right_sum = sum_of_subtrees(root.right)
    
    # Check if the root's value equals the sum of the left and right subtree values
    return root.val == left_sum + right_sum
```
 
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with an input to check for the expected output.
- Example: Trace with root = [10, 4, 6]
    - left_sum = 4, right_sum = 6
    - root.val = 10
    - root.val == left_sum + right_sum (10 == 4 + 6) -> True

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

Assume `N` represents the number of nodes in the tree.

* **Time Complexity**: `O(N)` because we need to visit each node once to calculate the sums.
* **Space Complexity**: `O(H)` where `H` is the height of the tree, representing the space on the call stack due to recursion.