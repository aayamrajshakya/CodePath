*[[Unit 2 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** First, collect all the scores for each team into lists.  Then divide by the number of games to find the average score.

```markdown
# Step 1: Get all team scores together 

1) Create an empty "scores" dict to hold a list of scores for each team
2) For each "game" dict in the the input
  a) If team is not in "scores":
    i) Map team -> empty list in "scores"
  b) Append score to team -> list in "scores"

# Step 2: Find the highest average score

3) Highest average starts at 0, best team starts at None
4) For each team, score-list in "scores" dict
  a) Get average of score-list
  b) If average is higher than current highest
    i) Replace current highest
   ii) Update best team
5) Return best team
```

## I-mplement

```python
def team_with_best_average_score(games):
    """
    Returns the team with the highest average score from a list of dictionaries representing games.
    Each dictionary contains the team's name and the score they achieved in a game.
    """
    team_scores = {}
    for game in games:
        team = game['team_name']
        score = game['score']
        if team not in team_scores:
            team_scores[team] = []
        team_scores[team].append(score)
    
    highest_avg_score = 0
    best_team = None
    for team, scores in team_scores.items():
        avg_score = sum(scores) / len(scores)
        if avg_score > highest_avg_score:
            highest_avg_score = avg_score
            best_team = team
    
    return best_team
``` 