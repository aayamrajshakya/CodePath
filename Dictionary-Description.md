*[[Unit 2 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Find the bug in the provided code!

**⚠️ Common Mistakes**

- Don't just change the input to make it work -- change the function `get_description` so that it can safely handle the situation.

## I-mplement

```python
def get_description(info, keys):
    for key in keys:
	    if key in info:
		    print(info[key])
            else:
	            print(None)
``` 