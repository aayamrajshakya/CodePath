_[[Unit 5 Session 1]] (Click for link to problem statements)_

## U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What should be returned if no Pokemon match the given type?
  - An empty list should be returned to indicate no matches.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Traverse the list of Pokemon instances to find and collect those that match the specified type.

```markdown
1. Create an empty list called `have_type` to store Pokemon instances that match the given type.
2. Iterate through the list `my_pokemon`.
3. For each Pokemon, check if `pokemon_type` is in their types list.
4. If it is, add the Pokemon instance to the `have_type` list.
5. Return the `have_type` list containing all matching Pokemon.
```

**⚠️ Common Mistakes**

- Neglecting to check for type presence in the types list properly.
- Returning incorrect data types or failing to return anything at all.

## I-mplement

```python
def find_pokemon(my_pokemon, pokemon_type):
    have_type = []

    for pokemon in my_pokemon:
        if pokemon_type in pokemon.types:
            have_type.append(pokemon)

    return have_type


## Testing example:
have_type = find_pokemon(my_pokemon, pokemon_type)
for pokemon in have_type:
    print(pokemon.name)
```
