*[[Unit 3 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What if n is larger than the number of characters in the string?
  - This won't be the case, 1 <= n <= len(str).

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Slide the input string into two components and then combine them at the end.

```markdown
1) Slice the second half of the string (the characters from n onward)
2) Slice the first half of the string (the characters up to n)
3) Return these two components added together in the order: second, first
```

## I-mplement

```python
def rotate_left(s, n):
    return s[n:] + s[:n]
```