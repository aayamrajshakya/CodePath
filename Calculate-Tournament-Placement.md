*[[Unit 5 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- How should ties in average race outcomes be handled?
  - Tied averages should not affect the ranking of a player whose average is not surpassed.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Calculate the current player's average race outcome and compare it against each opponent's average to determine the tournament ranking.

```markdown
1) Compute the average race outcome for the current player.
2) Initialize a ranking counter starting at 1, considering the current player as potentially the best until compared.
3) Loop through each opponent to compute their average race outcomes.
4) For each opponent, if their average is lower (better) than the current player's, increment the current player's rank.
5) Return the calculated rank, reflecting how many players performed better on average.
```

**⚠️ Common Mistakes**

- Mistakenly counting ranks or not accounting for opponents who have exactly the same average, which should not decrease the player's rank. 

## I-mplement

```python
class Player:
    def __init__(self, character, kart, outcomes):
        self.character = character
        self.kart = kart
        self.items = []
        self.race_outcomes = outcomes

    def get_tournament_place(self, opponents):
        # Calculate own average race outcome
        own_average = sum(self.race_outcomes) / len(self.race_outcomes) if self.race_outcomes else float('inf')
        
        # Start counting at 1 for the player themselves
        rank = 1
        
        # Calculate and compare with each opponent's average race outcome
        for opponent in opponents:
            opponent_average = sum(opponent.race_outcomes) / len(opponent.race_outcomes)
            if opponent_average < own_average:
                rank += 1 # The opponent did better (lower) than we did!
        
        return rank
```