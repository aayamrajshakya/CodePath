*[[Unit 3 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Will the string ever be empty?
  - Potentially, yes. Your code should allow for this.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Slice the input string into three components and then combine them at the end.

```markdown
1) Slice the last character from the input string
2) Slice the middle (excluding the first and last) characters from the input string
3) Slice the first character from the input string
4) Return these three components added together in the order: last, middle, first
```

## I-mplement

```python
def swap_ends(myStr):
    return myStr[-1:] + myStr[1:-1] + myStr[:1]
```