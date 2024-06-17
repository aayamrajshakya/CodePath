*[[Unit 1 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Should the function always print the same food item?
  - No.  It should print whatever food item was used when the function was called.
- Does it matter which emoji I use?
  - Not really, but the output will make more sense if you use a food emoji.
- Should the variable menu be set inside of the function definition or passed as a parameter?
  - The menu item is passed as a parameter and does not need to be defined inside the function definition.
   
## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use the provided function to print out an emoji representing today's lunch. The function is already defined for you, so your job is to call it and give it the menu item you'd like.

## I-mplement

```python
def print_menu(menu):
  print("Lunch today is: " + menu)

print_menu("🍕")
```