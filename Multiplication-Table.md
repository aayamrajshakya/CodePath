*[[Unit 1 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
  
- Will the number always be an integer?
  - Yes.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Loop from 1 to 10, and print the result of multiplying by `n` each time.

**⚠️ Common Mistakes**

- Make sure your loop doesn't exclude the last value (10).  

## I-mplement

```python
def multiplication_table(n):
	for multiplicand in range(1, 11):
		print(n * multiplicand)
```