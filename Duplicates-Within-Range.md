*[[Unit 4 Session 2]] (Click for link to problem statements)*

## U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- How does the function behave when k is zero?
  - The function should return False unless there are repeated elements consecutively in the list.
- What if the list is empty?
  - The function should return False as there are no elements to form duplicates.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use a dictionary to track the indices of elements as you iterate through the list. For each element, check if it has appeared before within the distance k.

```markdown
1) Create a dictionary to store each element's last seen index.
2) Iterate through the list:
  a) If the element is already in the dictionary and the difference between the current index and the last seen index is less than or equal to k, return True.
  b) Update the dictionary with the current index for the element.
3) If the loop completes without finding any nearby duplicates, return False.
```

**⚠️ Common Mistakes**

- Forgetting to update the dictionary with the most recent index of each element.
- Incorrectly calculating the distance between indices which might lead to false positives or negatives.

## I-mplement

```python
def contains_nearby_duplicate(lst, k):
    # Dictionary to store the elements and their last seen indices
    element_indices = {}
    # Loop through the array
    for i, element in enumerate(lst):
        # Check if the element is in the dictionary and within the k distance
        if element in element_indices and i - element_indices[element] <= k:
            return True
        # Update the dictionary with the current index of the element
        element_indices[element] = i
    return False
```