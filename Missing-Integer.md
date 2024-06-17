*[[Unit 3 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Will there be more than one missing integer?
  - No.
- Will the list always start at 1?
  - Not necessarily!  Start counting from first element in the list.
- What if there is no missing integer?
  - In that case, you'll return the number after the final element in the list.  

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Compare each value to its index -- if it's not equal to the index + 1, we found the missing number.

```markdown
1) Create an index variable at 0
2) While index is valid for our list
  a) Is list[index] same as index + 1?
    i) If yes, move on to next index
   ii) If not, index+1 is our missing value
3) 
```

**⚠️ Common Mistakes**

- 

## I-mplement

```python

```