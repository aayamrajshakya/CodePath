*[[Unit 1 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Should the function always print the same mood?
  - Yes.
- Should the mood variable be updated inside the function definition or passed as a parameter
  - The mood variable is set inside the function definition
- Does the function require any parameters when being called?
  - No, the function does not require any parameters as indicated by the lack of a variable name in the signature todays_mood()

   
## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Make a function that prints an emoji representing today's mood.

```markdown
1) Create a new function by writing a function signature
2) Create a variable to store the current mood emoji
3) Print "Today's mood:" followed by the value of the variable
3) Call the created function
```

**⚠️ Common Mistakes**

- Emojis are considered characters by python, and thus need to be put in quote-marks, like strings.

## I-mplement

```python
def todays_mood():
	mood = "🥱" 
	print("Today's mood: " + mood)

todays_mood()
```