*[[Unit 2 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Check if the book is already in the dictionary, add them if not, then increment their quantity by 1.

```markdown
1) If the book is a key in the dict, increment the value by 1
2) Otherwise, map book -> 1 in the dict
```

## I-mplement

```python
def return_book(borrowed_books, book):
    if book in borrowed_books:
        borrowed_books[book] += 1
    else:
        borrowed_books[book] = 1
    return borrowed_books
```