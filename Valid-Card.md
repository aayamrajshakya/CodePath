*[[Unit 5 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- How do we ensure the Card class can validate itself based on the suit and rank?
  - By implementing an `is_valid()` method that checks if the card's suit and rank are within predefined lists of acceptable values.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Add a method to the Card class that validates whether the card's suit and rank are among those traditionally recognized in a standard deck.

```markdown
1) Define acceptable suits and ranks within the `is_valid` method.
2) Check if the card's suit is within the allowed suits and the rank is within the allowed ranks.
3) Return True if both conditions are met; otherwise, return False.
```

**⚠️ Common Mistakes**

- Not correctly checking membership within the lists of suits and ranks.
- Improper use of return statements which could lead to premature or incorrect returns.

## I-mplement

```python
class Card():
    def  __init__(self, suit, rank):
        self.suit = suit
        self.rank = rank
        
    def is_valid(self):
        suits = ['Hearts', 'Diamonds', 'Clubs', 'Spades']
        ranks = ['2', '3', '4', '5', '6', '7', '8', '9', '10', 'Jack', 'Queen', 'King', 'Ace']
        if self.suit in suits and self.rank in ranks:
            return True
        return False
```