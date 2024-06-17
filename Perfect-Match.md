*[[Unit 3 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- When we call the function, what will that input parameter be used for?
  - It will be the dictionary the loop iterates over.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Call the function with the input dictionary.

```markdown
1) Extract the unique parts of each string (there will be two)
2) Create a dictionary with the first parts as the keys and the second as the values
3) Call the function with the dictionary as the input
```

## I-mplement

```python
match_made({"Peanut butter": "Jelly", "Spongebob": "Patrick", "Ash": "Pikachu"})
```