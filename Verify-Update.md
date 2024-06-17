*[[Unit 5 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- How does changing an attribute affect the instance of a class?
  - Changing an attribute directly affects the instance's current state, and subsequent method calls will reflect this change.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Modify the `suit` attribute of the existing `Card` instance and verify the update by printing the card's details.

```markdown
1) Update the `suit` attribute of the `card` object to "Hearts".
2) Use the `print_card()` method to output the updated state of the card, ensuring it now shows "Hearts" instead of "Clubs".
```

**⚠️ Common Mistakes**

- Misunderstanding the property names of the class, potentially attempting to update a non-existent property.
- Not using the class's methods to verify changes, leading to unclear confirmation of the update.

## I-mplement

```python
card.suit = "Hearts"
card.print_card()
```