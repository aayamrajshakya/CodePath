*[[Unit 2 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What if the list is empty?
  - In this case, there is no majority element, so return `None`.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Create a frequency map for each element in the list.  If the frequency ever gets larger than n/2, we found the majority element.

```markdown
1) Create an empty dict for the frequency map
2) For each element in the list
  a) If it's not in the frequency map, add it with initial count of 0
  b) Regardless, now increment the count by 1
  c) If the count is greater than n/2, return the element
3) Never found anything, so return None
```

## I-mplement

```python
def find_majority_element(elements):
    freq_map = {}
    for element in elements:
        if element not in freq_map:
            freq_map[element] = 0
        freq_map[element] += 1
        if freq_map[element] > len(elements) / 2:
            return element
    return None
``