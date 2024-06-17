*[[Unit 3 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Will the input list ever be empty?
  - Potentially, yes. We will want to allow for this case.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Convert each string in the input list to an integer and keep an updated total sum to return at the end.

```markdown
1) First, set a sum variable to 0 that we will add to and return later
2) Loop through each string in the list
  a) Convert the string to an integer and add it to the sum
3) Return the total sum
```

## I-mplement

```python
def sum_of_number_strings(s):
    total_sum = 0
    for num_str in s:
        total_sum += int(num_str)
    return total_sum
```