*[[Unit 5 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What should occur when a Pokemon's attack reduces another Pokemon's health to zero or less?
  - The opponent's health should be set to zero and it should be indicated that they have fainted.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Implement the `attack` method in the `Pokemon` class to decrease the opponent's `hp` by the attacking Pokemon's `damage`. Check if this results in the opponent fainting or just losing some health.

```markdown
1) Define the `attack` method that accepts another `Pokemon` object as an `opponent`.
2) Subtract the attacking Pokemon's `damage` from the opponent's `hp`.
3) Check if the opponent's `hp` is 0 or less:
   - If yes, set the `hp` to 0 and print "<opponent name> fainted".
   - If no, print "<Pokemon name> dealt <damage> damage to <opponent name>".
```

**⚠️ Common Mistakes**

- Not properly handling the case where the opponent's `hp` goes below zero.
- Incorrect calculation of damage or wrong attribute usage, resulting in incorrect game mechanics.

## I-mplement

```python
class Pokemon():
	def  __init__(self, name, hp, damage):
		self.name = name
		self.hp = hp # hit points
		self.damage = damage # The amount of damage this pokemon does to its opponent every attack
		
	
	def attack(self, opponent):
		opponent.hp -= self.damage
		if opponent.hp <= 0:
			opponent.hp = 0
			print(f"{opponent.name} fainted")
		else:
			print(f"{self.name} dealt {self.damage} damage to {opponent.name}")
		
```