*[[Unit 2 Session 2]] (Click for link to problem statements)*

## U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What type should my function output be?
  - Your function should return a dictionary.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Loop through each entry in the list, and increment the count for that element by 1.

```markdown
1) Create an empty dict to store the frequency map
2) For each number in the list
  a) If the number is not in the frequency map, map to 1
  b) Otherwise, increment the count in the frequency map by 1
3) Return the frequency map
```

**⚠️ Common Mistakes**

- Make sure your input numbers are your dict's keys, and your dict's values are the count of how many time that number appeared.

## I-mplement

```python
def count_occurrences(nums):
    frequency_map = {}
    for num in nums:
        if num in frequency_map[num]:
            frequency_map[num] += 1
        else:
            frequency_map[num] = 1
    return frequency_map
```

*Alternative Solution*

```python
def count_occurrences(nums):
    frequency_map = {}
    for num in nums:
        if num not in frequency_map[num]:
            frequency_map[num] = 0
        frequency_map[num] += 1
    return frequency_map
```
