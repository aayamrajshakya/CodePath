*[[Unit 5 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What if the starting Pokemon has no evolutionary line?
  - The function should still return a list containing only the starter Pokemon.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Traverse through the evolutionary chain of the given Pokemon and compile a list of all forms from the starter to its final evolution.

```markdown
1) Initialize a list `evolution` with the `starter_pokemon` as its first element.
2) Set a variable `current_pokemon` to the `starter_pokemon`.
3) Use a while loop to follow the evolution chain:
  a) While `current_pokemon.evolution` is not None:
    i) Append the next evolution to the `evolution` list.
   ii) Move to the next Pokemon in the evolutionary line by setting `current_pokemon` to `current_pokemon.evolution`.
4) Return the `evolution` list containing the starter Pokemon and all its evolutions.
```

**⚠️ Common Mistakes**

- Forgetting to handle cases where a Pokemon does not evolve.
- Failing to update the current_pokemon variable within the loop, which could lead to an infinite loop.

## I-mplement

```python
def evolve(starter_pokemon):
  evolution = [starter_pokemon]

  current_pokemon = starter_pokemon
  while current_pokemon.evolution:
    evolution.append(current_pokemon.evolution)
    current_pokemon = current_pokemon.evolution

  return evolution
  
# Testing:
evolution = evolve(charmander)
for pokemon in evolution:
  print(pokemon.name)
```