*[[Unit 1 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Create a reversed list by looping through each element and adding them to the beginning of another list.

```markdown
1) Create a new list to hold the reversed values
2) Loop through each value in the original list
  a) Add each value to the BEGINNING of the new list
3) Return the new list
```

**⚠️ Common Mistakes**

- To visualize this strategy, it might help to try drawing out an example.
  - You've most likely reversed a "list" using this strategy in real life.  For example, have you ever had to reverse the order of a stack of papers?  How did you do it?

## I-mplement

```python
def reverse_list(numbers):
    reversed_list = []
    for number in numbers:
        reversed_list.insert(0, number)
    return reversed_list
```