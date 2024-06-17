*[[Unit 10 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 20 mins
* 🛠️ **Topics**: Linked List, Two Pointers
    
## 1: U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- What should be returned if the two linked lists do not intersect?
    - None, since there is no intersection node.

```
HAPPY CASE
Input: listA = [4, 1, 8, 4, 5], listB = [5, 6, 1, 8, 4, 5]
Output: Reference to node with value 8
Explanation: The two lists intersect at node with value 8.

HAPPY CASE
Input: listA = [1, 9, 1, 2, 4], listB = [3, 2, 4]
Output: Reference to node with value 2
Explanation: The two lists intersect at node with value 2.

EDGE CASE
Input: listA = [2, 6, 4], listB = [1, 5]
Output: None
Explanation: The two lists do not intersect.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

For Linked List problems, we want to consider the following approaches:

- Using two pointers to traverse both lists and find the intersection.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use two pointers to traverse both linked lists. When one pointer reaches the end of a list, switch it to the head of the other list. If the lists intersect, the pointers will eventually meet at the intersection node.

```
1) Initialize two pointers, pointer_a and pointer_b, to the heads of the two linked lists.
2) Traverse the lists until the two pointers meet:
    a) If pointer_a reaches the end of listA, switch it to the head of listB.
    b) If pointer_b reaches the end of listB, switch it to the head of listA.
    c) Move both pointers one step forward.
3) The meeting point of the two pointers is the intersection node, or None if they do not intersect.
4) Return the intersection node.
```

**⚠️ Common Mistakes**

- Not correctly handling the case where the lists do not intersect.
- Forgetting to switch the pointers when they reach the end of a list.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```
def find_intersection(headA, headB):
    if not headA or not headB:
        return None

    pointer_a = headA
    pointer_b = headB

    # Loop until the two pointers meet or both reach the end
    while pointer_a is not pointer_b:
        # If reaching the end of one list, switch to the head of the other list
        pointer_a = pointer_a.next if pointer_a else headB
        pointer_b = pointer_b.next if pointer_b else headA

    # This will be either the intersection node or None
    return pointer_a
```
 
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with an input to check for the expected output.
- Example: Trace with listA = [4, 1, 8, 4, 5], listB = [5, 6, 1, 8, 4, 5]
    - pointer_a = 4, pointer_b = 5
    - pointer_a = 1, pointer_b = 6
    - pointer_a = 8, pointer_b = 1
    - pointer_a = 4, pointer_b = 8
    - pointer_a = 5, pointer_b = 4
    - pointer_a = None, pointer_b = 5
    - pointer_a = 5 (headB), pointer_b = None
    - pointer_a = 6, pointer_b = 4 (headA)
    - pointer_a = 1, pointer_b = 1
    - pointer_a = 8, pointer_b = 8 (intersection)

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

Assume `N` and `M` represent the lengths of the two linked lists.

* **Time Complexity**: `O(N + M)` because we may need to traverse both lists.
* **Space Complexity**: `O(1)` because we only use a constant amount of extra space.