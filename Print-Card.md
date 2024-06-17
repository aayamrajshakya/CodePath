*[[Unit 5 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What is expected to be printed when calling `print_card()`?
  - The method prints cards in the format "Ace of Clubs".

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Instantiate a `Card` object with specified attributes and use a method to display its properties.

```markdown
1) Create a `Card` instance with the suit "Clubs" and the value "Ace".
2) Store this instance in a variable named `card`.
3) Call the `print_card()` method on the `card` instance to display the card's details.
```

**⚠️ Common Mistakes**

- Not correctly instantiating the Card object with the correct attributes.
- Failing to call the `print_card()` method.

## I-mplement

```python
card = Card("Clubs", "Ace")
card.print_card()
```