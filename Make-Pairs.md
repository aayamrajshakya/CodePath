*[[Unit 2 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Will the list ever be empty?
  - No.  You can assume it has at least 2 numbers.
- Will the list ever have an odd number of entries?
  - No.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** In order to be able to make pairs, every element in the list most occur an even number of times.  Use a frequency map to check for that!

```markdown
1) Create an empty dict for the frequency map
2) For each num in the list:
  a) Add 1 to the current frequency map value (default to 0)
3) For each count in the frequency map values:
  a) If the count is odd, return False
4) All counts were even, so return True
```

**⚠️ Common Mistakes**

- To get an element from a dict with a default fallback value, try looking up the `get()` function.

## I-mplement

```python
def divideArray(nums):
    # Frequency map to count occurrences of each number
    frequency_map = {}
    for num in nums:
        frequency_map[num] = frequency_map.get(num, 0) + 1
    
    # Check if all counts are even
    for count in frequency_map.values():
        if count % 2 != 0:
            return False  # An odd count found, can't divide into pairs
    
    return True  # All counts are even, can divide into pairs
``