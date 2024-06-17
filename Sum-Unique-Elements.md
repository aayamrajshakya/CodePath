*[[Unit 3 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What if `lst1` is empty?
  - In this case, the total sum of elements is 0.
- What if `lst2` is empty?
  - In this case, you don't need to worry about `lst1` elements appearing in `lst2`.  But you still need to check if elements occur more than once in `lst1`!

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Create a frequency map of elements across both lists, then add up any element in `lst1` with a frequency of 1.

```markdown
1) Create a frequency map¹ for all elements across both lists
2) For each element in lst1, if the frequency is 1, add to sum
3) Return the sum
```
*¹ see [[Frequency Count]] for psuedocode*

**⚠️ Common Mistakes**

- Two separate frequency maps will slow down your solution -- how can you do it with just one?

## I-mplement

```python
def sum_of_unique_elements(lst1, lst2):
    count = {}
    for num in lst1 + lst2:
        if num in count:
            count[num] += 1
        else:
            count[num] = 1
    sum_unique = 0
    for num in lst1:
        if count[num] == 1:
            sum_unique += num
    return sum_unique
```