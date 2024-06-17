*[[Unit 5 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- How should the get_player() method format the output for each player?
  - It should return the string describing the player and their kart in a format ready for concatenation in the match description.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Create a second Player instance and use a method to format a match description string that includes both players.

```markdown
1) Instantiate a second Player object with "Bowser" as the character and "Pirahna Prowler" as the kart, storing it in `player_two`.
2) Utilize the `get_player()` method for both instances to generate a formatted match description.
```

**⚠️ Common Mistakes**

- Using incorrect string formatting syntax, which could lead to errors or unintended output.


## I-mplement

```python
player_two = Player("Bowser", "Pirahna Prowler")
print(f"Match: {player_one.get_player()} vs {player_two.get_player()}")
```