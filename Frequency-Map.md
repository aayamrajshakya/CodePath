*[[Unit 6 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 20 mins
* 🛠️ **Topics**: Linked Lists, Dictionaries
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: Can the list be empty?
    - A: Yes, handle this case by returning an empty dictionary.

```markdown
HAPPY CASE
Input: 1 -> 2 -> 2 -> 3
Output: {1: 1, 2: 2, 3: 1}
Explanation: The frequencies of the elements are correctly counted.

EDGE CASE
Input: None
Output: {}
Explanation: The list is empty, so no frequencies to count.
```   

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

For element frequency problems, we want to consider the following approaches:

- Use a dictionary to keep track of data and its frequency.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Traverse the linked list and store each element's frequency in a dictionary.

```markdown
1) Initialize an empty dictionary `freq`.
2) Traverse the linked list from the head to the end.
3) For each node, check if its value is already in `freq`.
    - If yes, increment the corresponding frequency.
    - If no, add the value to the dictionary with a frequency of 1.
4) Continue until all nodes are processed.
5) Return the `freq` dictionary.
```

**⚠️ Common Mistakes**

- Forgetting to handle the case where the list is empty.
- Miscounting elements by not checking existing keys correctly.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def frequency_map(head):
    freq = {}  # Dictionary to store frequency of each element
    current = head
    while current:
        if current.value in freq:
            freq[current.value] += 1  # Increment count of the value
        else:
            freq[current.value] = 1  # Initialize count of the value
        current = current.next
    return freq
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with an input to check for the expected output
- Catch possible edge cases and off-by-one errors

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

Assume `N` represents the number of nodes in the linked list.

* **Time Complexity**: `O(N)` because we traverse through the entire list once to count frequencies.
* **Space Complexity**: `O(N)` in the worst case, where all elements are unique and need individual entries in the dictionary.
