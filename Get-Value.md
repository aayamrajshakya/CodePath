*[[Unit 5 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What should the `get_value()` method do if the card is found to be invalid?
  - It should return `None`, as specified in the problem statement.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Implement a `get_value()` method that first checks if a card is valid and then returns its numerical value based on the rank.

```markdown
1) Use the `is_valid()` method to determine if the card is valid.
2) If invalid, return `None`.
3) If the rank is 'Ace', return 1.
4) If the rank is 'Jack', return 11.
5) If the rank is 'Queen', return 12.
6) If the rank is 'King', return 13.
7) For numeric ranks ('2' to '10'), convert the rank to an integer and return.
```

**⚠️ Common Mistakes**

- Failing to first check the validity of the card before attempting to assign a value.
- Incorrect conversion or mapping of face card names to their respective values.

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
      
    def get_value(self):
    
        if not self.is_valid():
            return None
        elif self.rank == 'Jack':
            return 11
        elif self.rank == 'Queen':
            return 12
        elif self.rank == 'King':
            return 13
        elif self.rank == 'Ace':
            return 1
        else:
            return int(self.rank)
      
```