*[[Unit 2 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Loop through each book, find its average rating, and add the pair to a new dictionary.

```markdown
1) Create an empty dict for average ratings
2) For each book and ratings list in the input dict
  a) Find the average of the ratings list
  b) Map book -> average in the new average dict
3) Return the new average dict
```

## I-mplement

```python
def average_book_ratings(book_ratings):
    avg_ratings = {}
    for book, ratings in book_ratings.items():
        avg_ratings[book] = sum(ratings) / len(ratings)
    return avg_ratings
``` 