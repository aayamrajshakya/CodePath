*[[Unit 1 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Will the `service_quality` always be "poor", "average", or "excellent"?
  - No.  Your code should return `None` in the case of an invalid quality.
  
## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Calculate the appropriate tip based on the bill and quality of service.

```markdown
1) Create a new function with parameters for the bill and service quality
2) Check if the quality matches each possible value
   a) If it matches, calculate the tip amount and return it
   b) If it doesn't match, check the next possible quality value
3) If no quality matched, return None
```

## I-mplement

```python
def calculate_tip(bill, service_quality):
	if service_quality == "poor":
		return bill * .1
	elif service_quality == "average":
		return bill * .15
	elif service_quality == "excellent":
		return bill * .2
	else:
		return None
```