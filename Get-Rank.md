*[[Unit 5 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- How is the order of players determined in this context?
  - Each player has an `ahead` attribute pointing to the player directly ahead of them in the race. This linked structure helps to determine their position.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Traverse the linked list structure formed by the `ahead` attributes of Player objects to determine the position of `my_player` in the race.

```markdown
1) Initialize a counter `place` to 1, as the player is at least in the race.
2) Start with `current` pointing to `my_player`.
3) Traverse the list by following the `ahead` pointers, incrementing `place` until there are no more `ahead` pointers (i.e., until reaching the race leader).
4) Return the `place` number, which indicates the player's position in the race.
```

**⚠️ Common Mistakes**

- Incorrectly initializing the starting place, potentially off by one error.
- Failing to correctly follow the ahead pointers, which could either loop indefinitely or stop prematurely.

## I-mplement

```python
def get_place(my_player):
    place = 1  # Start counting from 1 as the player is at least in some place
    current = my_player
    while current.ahead:
        place += 1
        current = current.ahead
    return place
```