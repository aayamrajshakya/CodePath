*[[Unit 2 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Create a frequency map, then create an inverted version -- so the frequencies are KEYS and the values are a list of nums with that frequency.

```markdown
1) First, create a frequency map for the list¹
2) Next, create an empty dict to hold our inverted map
3) Loop through each num, frequency in frequency map:
  a) If the frequency is not in inverted map
    i) Map it to an empty list
  b) Add the num to the inverted dict's list for that frequency
4) Return the inverted map
```
*¹ see [[Frequency Count]] for psuedocode*

## I-mplement

```python
def group_by_frequency(lst):
    # Step 1: Count the frequency of each element
    frequency_map = {}
    for element in lst:
        if element in frequency_map:
            frequency_map[element] += 1
        else:
            frequency_map[element] = 1
    
    # Step 2: Invert the mapping from element:frequency to frequency:[elements]
    inverted_map = {}
    for element, freq in frequency_map.items():
        if freq not in inverted_map:
            inverted_map[freq] = []
        inverted_map[freq].append(element)
    
    # Step 3: Ensure the elements in the inverted map are sorted by their first appearance
    # This is inherently maintained as we append elements in the order we traverse them
    return inverted_map
```