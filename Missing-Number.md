*[[Unit 1 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Will the list ever contain duplicate numbers?
  - No.  Each number in the list will be distinct.
- Will there ever be multiple missing numbers?
  - No.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Loop through the list from smallest to largest, and use a counter variable to try counting up with each element.

```markdown
1) First, sort the list from smallest to largest
2) Create a counter variable starting at zero
3) For each element in the list
  a) Check if it matches the counter
  b) If it does, all is well -- so add 1 to the counter
  c) If not, this is the missing number, and the counter will stay as is
4) When the loop is finished, return the counter's value
```

## I-mplement

```python
# Example Input: nums = [3,0,1]
# Expected Output: 2

def find_missing(nums):
    nums.sort()
    counter = 0
    for num in nums:
        if num == counter:
            counter += 1 
    return counter
```

Alternatively, a slightly more time-efficient solution is possible using the `break` statement to exit the loop early once the missing number is found:

```python
# Example Input: nums = [3,0,1]
# Expected Output: 2

def find_missing(nums):
    nums.sort()
    counter = 0
    for num in nums:
        if num == counter:
            counter += 1 
        else:
            break # Do not need to keep looping
    return counter
```
