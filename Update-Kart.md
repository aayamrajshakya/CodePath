*[[Unit 5 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What needs to be updated for player_one?
  - The `kart` attribute of player_one needs to be updated to a new value, "Dolphin Dasher".

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Directly modify the `kart` attribute of the `player_one` object to change its value.

```markdown
1) Access the `kart` attribute of `player_one`.
2) Update the attribute to the new value "Dolphin Dasher".
```

**⚠️ Common Mistakes**

- Incorrectly referencing the attribute to be changed.
- Failing to correctly assign the new value, potentially leading to no change or an error.

## I-mplement

```python
player_one.kart = "Dolphin Dasher"
```