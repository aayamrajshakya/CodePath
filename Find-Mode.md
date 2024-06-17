*[[Unit 2 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What should my program do if the list is empty?
  - In that case, return `None`.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Create an occurrence dict counting how many times each element appears in the list, and also keep track of the highest occurrence so far.

```markdown
1) Create an empty dict to store the occurrences
2) Assume max_count is 0, most_frequent is None
3) For each number in the list
  a) Is the number in the occurrences dict?
      i) If yes, increment count by 1
     ii) Otherwise, map number -> 1
  b) Regardless, check if this is our new max_count
     i) If so, update max_count and most_frequent
4) Return the most_frequent 
```

## I-mplement

```python
def find_mode(lst):
    frequency_map = {}
    max_count = 0
    most_frequent = None
    for num in lst:
        if num in frequency_map:
	    frequency_map[num] += 1
	else:
	    frequency_map[num] = 1			  
        if frequency_map[num] > max_count:
            max_count = frequency_map[num]
            most_frequent = num
    return most_frequent
```