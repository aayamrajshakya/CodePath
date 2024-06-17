*[[Unit 1 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Will the input always be a number?
  - Yes.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Create a function that converts a Celsius temperature into Kelvin and Fahrenheit.

```markdown
1) Create an empty list to store the output.
2) Calculate the Kelvin and Fahrenheit values
3) Add each value to the end of the output list 
4) Return the output list
```

**⚠️ Common Mistakes**

- Make sure you pay attention to order of operations!
- What temperature system is your initial input in?  

## I-mplement

```python
def convertTemp(celsius):
	output = []
	kelvin = celsius + 273.15
	fahrenheit = celsius * 1.8 + 32.0
	
	output.append(kelvin)
	output.append(fahrenheit)
	return output
```