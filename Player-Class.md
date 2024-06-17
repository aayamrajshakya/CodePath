*[[Unit 5 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What attributes does the Player class require for instantiation?
  - The Player class requires a character name and a kart model for instantiation.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use the provided Player class constructor to create a new instance with specific attributes.

```markdown
1) Instantiate a Player object with "Yoshi" as the character and "Super Blooper" as the kart.
2) Store this object in a variable named `player_one`.
```

**⚠️ Common Mistakes**

- Misplacing the order of parameters when calling the constructor.
- Incorrectly spelling the parameters' values.

## I-mplement

```python
player_one = Player("Yoshi", "Super Blooper")
```