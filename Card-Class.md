*[[Unit 5 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Are there specific constraints on the values for suit or rank?
  - Typically, card suits and ranks are predefined, but no specific constraints are given here other than using "Spades" and "8".

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Create an instance of the `Card` class using the provided suit "Spades" and rank "8".

```markdown
1) Instantiate an object of the `Card` class with "Spades" for the suit and "8" for the rank.
2) Store the instance in a variable named `card`.
```

**⚠️ Common Mistakes**

- Incorrectly passing parameters to the class constructor.
- Misnaming the variables or class leading to runtime errors.

## I-mplement

```python
card = Card("Spades", "8")
```