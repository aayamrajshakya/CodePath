*[[Unit 2 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Is it possible for the list to be empty?
  - Yes.  In that case, your code should return `None`.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Loop through a list of dictionaries and find the one with the highest value for "rating".

```markdown
1) If the list is empty, return None
2) Assume the first book is the highest rated (so far)
3) For each book after the first:
  a) If the book has a higher rating, set that book
     as the new highest rated
4) Once all books are checked, return the highest rated book we found
```

**⚠️ Common Mistakes**

- Pay attention to your syntax and make sure you return the entire book, not just its rating!

## I-mplement

```python
def highest_rated(books):
    """
    Returns the book with the highest rating from 
    a list of dictionaries representing books.
    Each dictionary contains the book's title, author, and rating.
    """
    if not books:  # Check if the list is empty
        return None

    highest_rated_book = books[0]  # Assume the first book is the highest rated initially
    for book in books[1:]:  # Start checking from the second book
        if book['rating'] > highest_rated_book['rating']:
            highest_rated_book = book  # Update the highest rated book

    return highest_rated_book
``` 