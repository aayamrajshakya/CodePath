*[[Unit 1 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
  
## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Loop from 5 to 100, stepping up by 5 each time.

**⚠️ Common Mistakes**

- Make sure your loop doesn't exclude the last value (100).  

## I-mplement

```python
# Output:
# 5
# 10
# 15
# 20
# 25
# 30
# 35
# 40 ....
# 100

def multiples_of_five(start, stop):
	for num in range(5, 101, 5):
		print(num)
```