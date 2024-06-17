*[[Unit 5 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What is the format for representing a card in the list? Should it be the card object or a string representation of the card?
  - The problem solution uses the card object itself, but typically, a string representation could be used for clearer output.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Traverse the linked list of cards starting from a given card, collecting all cards until no more cards are linked (i.e., `next` is `None`).

```markdown
1) Start with the provided `starting_card`.
2) Initialize an empty list `cards` to hold the cards encountered.
3) Use a while loop to traverse the linked cards:
  a) Append the current card to the `cards` list.
  b) Move to the next card by updating `current` to `current.next`.
4) Continue until `current` is `None` (indicating the end of the hand).
5) Return the list `cards`.
```

**⚠️ Common Mistakes**

- Forgetting to update the `current` card to the next in the loop, which would cause an infinite loop.


## I-mplement

```python
def print_deck(starting_card):
    cards = []
    current = starting_card
    while current:
        cards.append(current)
        current = current.next
    return cards
```