*[[Unit 1 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Will the input always be an integer?
  - Yes.
- Should the function print anything out?
  - Yes, print the results from inside the function.
  
## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Given a points total, print out the Blackjack game result.

```markdown
1) Set up the function:
  a) Create a new function with a parameter representing the score
  b) Check each condition and print the appropriate result
2) Test the function for all possible results by:
  a) Calling the function
```

## I-mplement

```python
def blackjack(score):
	if score < 17:
	    print("Hit Me!")
	elif score < 21:
	    print("Nice hand!")
	elif score >= 21:
	    print("Bust!")
	else:
	    print("Blackjack!")
	    
	    
blackjack(21) # Output: "Blackjack!"
blackjack(19) # Output: "Nice hand!"
blackjack(10) # Output: "Hit me!"
blackjack(25) # Output: "Bust!"
```