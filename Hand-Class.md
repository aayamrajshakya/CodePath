*[[Unit 5 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- How should the `Hand` class behave if trying to remove a card that isn't in the hand?
  - For this problem, you can assume the card is always in the hand when `remove_card` is called.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Develop a `Hand` class to manage a collection of `Card` objects, providing methods to add and remove cards.

```markdown
1) Initialize the `Hand` class with an empty list of cards.
2) Implement `add_card()` to append a `Card` object to the hand.
3) Implement `remove_card()` to remove a `Card` object from the hand.
```

**⚠️ Common Mistakes**

- Incorrect implementation of the list methods for adding or removing items.

## I-mplement

```python
class Hand:
    def __init__(self):
        self.cards = []

    def add_card(self, card):
        self.cards.append(card)

    def remove_card(self, card):
        self.cards.remove(card)
```