*[[Unit 1 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Will the player choices always be "rock", "paper", or "scissors"?
  - Yes.  They will also always be lowercase.
  
## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Calculate the appropriate tip based on the bill and quality of service.

```markdown
1) Create a new function with parameters for player1 and player2
2) If both players picked the same thing, print a tie message
3) Check if player2 picked "rock"
   a) If yes, and player1 picked "scissors", player2 wins
   b) If no, player1 wins 
     - (because we know they must have picked "paper")
4) Repeat step 3) for "scissors" and "paper"
```

## I-mplement

```python
def rock_paper_scissors(player1, player2):
	if player1 == player2:
	    print("It's a tie!")

	if player2 == "rock":
	    if player1 == "scissors":
	        print("Player 2 wins!")
	    else:
	        print("Player 1 wins!")
	
	if player2 == "paper":
	    if player1 == "scissors":
	      print("Player 2 wins!")
	    elif player1 == "rock":
	      print("Player 1 wins!")
```