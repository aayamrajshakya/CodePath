*[[Unit 5 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What format should be used to display the race results?
  - Each player's place in the race should be displayed followed by their character name.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Iterate through the list of Player objects and print each player's position in the race alongside their character name.

```markdown
1) Define the function `print_results` that takes a list `race_results` as its parameter.
2) Use a loop to iterate through the list, using `enumerate` to get both the index (place) and the Player object (racer).
3) Format the output to display the race position followed by the character name of each racer.
```

**⚠️ Common Mistakes**

- Starting the enumeration at 0 instead of 1, which would incorrectly number the racers starting from 0.
- Misprinting details such as racer name or position due to incorrect string formatting.

## I-mplement

```python
def print_results(race_results):
  for place, racer in enumerate(race_results, start=1):
    print(f"{place}. {racer.character}")
```