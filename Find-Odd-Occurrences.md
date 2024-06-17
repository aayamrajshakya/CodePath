*[[Unit 2 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Is it possible there will be multiple correct answers?
  - No.  You can assume each problem has exactly one solution.
- Does the order of the odd elements matter?
  - No.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** First, use a dict to count the occurrence of each element in the list.  Then find the elements that occurred an odd number of times, and return them as a list.

```markdown
1) Create an empty dict for occurrence map
2) For each element in the list
  a) If it's already in the dict, increment count by 1
  b) If it's not in the dict, map with an initial count of 1
3) Create an empty list for odd occurrence values
4) Loop through each number, count in the occurrences dict
  a) If an occurrence is odd, add to odds list
5) Return odds list
```

## I-mplement

```python
def find_odd_occurrences(numbers):

    # Dictionary to count occurrences
    count_map = {}
    for number in numbers:
        if number in count_map:
            count_map[number] += 1
        else:
            count_map[number] = 1
    
    # Find numbers with odd occurrences
    odd_occurrences = []
    for number, count in count_map.items():
        if count % 2 != 0:
            odd_occurrences.append(number)
    
    return odd_occurrences
```