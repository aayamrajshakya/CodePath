*[[Unit 2 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Will the points always be a positive integer?
  - Yes, but most solutions will work for negative point values too.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** If the player is already in the dict, add points to their score, otherwise, make a new entry in the dict for them.

```markdown
1) Check if player is in the dict
2) If so, add points to that player's current score
3) Otherwise, map player -> points in the dict
4) Return the updated dict 
```

**⚠️ Common Mistakes**

- If you try to ADD to a score for someone who is NOT already in the dict, you'll get a `KeyError`.

## I-mplement

```python
def update_score(scores, player, points):
    if player in scores:
        scores[player] += points
    else:
        scores[player] = points
    return scores
```