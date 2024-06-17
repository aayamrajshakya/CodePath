*[[Unit 2 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What if two genres have the same rating?
  - For simplicity's sake, you can assume no two genres will have the same rating.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Create two dictionaries: One mapping genre -> total points, and another mapping genre -> total movies.

```markdown
1) Create an empty ratings dict
2) Create an empty counts dict
3) For each movie in our input
  a) If genre already in our dicts
     i) Add the movie's rating to that genre's rating total
    ii) Add 1 to that genre's movie total
  b) Otherwise, add the rating as a new entry and set count to 1

4) Highest avg rating starts at 0
5) Loop through each genre
  a) Calculate the average using the ratings and counts for that genre
  b) If the avg is higher, make new highest avg
6) Return the name of the highest avg genre
```

**⚠️ Common Mistakes**

- When finding your highest average, make sure you keep track of genre names too, not just their average point totals!

## I-mplement

```python
def most_popular_genre(movies):
    """
    Returns the genre with the highest average rating from a list of dictionaries representing movies.
    Each dictionary contains the movie's title, genre, and rating.
    """
    genre_ratings = {}
    genre_counts = {}
    for movie in movies:
        curr_genre = movie['genre']
        if curr_genre not in genre_ratings:
            genre_ratings[curr_genre] = movie['rating']
            genre_counts[curr_genre] = 1
        else:
            genre_ratings[curr_genre] += movie['rating']
            genre_counts[curr_genre] += 1

    highest_avg_rating = 0
    most_popular = None
    for genre in genre_ratings:
        avg_rating = genre_ratings[genre] / genre_counts[genre]
        if avg_rating > highest_avg_rating:
            highest_avg_rating = avg_rating
            most_popular = genre

    return most_popular
``` 