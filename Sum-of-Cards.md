*[[Unit 5 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What should happen if there are no cards in the hand?
  - The function should return `0` as the sum, assuming all cards are valid or there are no cards.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Calculate the total value of all cards in a `Hand` instance, checking each card's validity before summing their values.

```markdown
1) Initialize a variable `total` to `0` to store the cumulative value of the cards.
2) Iterate over each card in the hand.
3) Check if the card is valid using the `is_valid()` method.
  a) If any card is invalid, immediately return `None`.
4) If the card is valid, add its value (obtained from `get_value()`) to `total`.
5) After all cards have been processed, return the value of `total`.
```

**⚠️ Common Mistakes**

- Neglecting to check the validity of each card, which could lead to adding incorrect values.
- Incorrectly handling or ignoring the None return condition for invalid cards.

## I-mplement

```python
def sum_hand(hand):
    total = 0
    for card in hand.cards:
        if not card.is_valid():
            return None
        total += card.get_value()
    return total
```