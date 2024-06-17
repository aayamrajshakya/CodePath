*[[Unit 1 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Will I need all 7 provided lines of code?
  - Yes.
- Will one line be used more than once? 
  - No, each line will be used only once.
- Are the lines already properly indented?
  - No, you will need to determine the appropriate indentation for each line.
   
## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Create a function that divides each value in a list by two.

```markdown
1) Declare the function signature with a parameter for the list
2) Create an empty list variable to hold the results
3) Loop through each element in the input list
  a) Divide the element in half
  b) Add the result to the "results" list
4) Return the results list
5) Call your function to test it with a sample list
```

## I-mplement

```python
def halve_list(lst): # Function signature
	result = [] # Create a list to store halved values
	for number in lst: # Loop through numbers in input list
		halved = number / 2 # Divide number by two
		result.append(halved) # Append halved number to end of input list
	return result # return result list

halve_list([2,4,6,8]) # Call the function
```