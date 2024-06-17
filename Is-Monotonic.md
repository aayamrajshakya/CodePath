*[[Unit 2 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Do I need to return anything different to distinguish between an increasing and decreasing list?
  - No.  In both cases, your function should return `True`.
- What if the list is empty?
  - In this case, return True.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Loop through each element in the list, and keep track of whether it consistently increases or descreases.

```markdown
1) By default, assume the list is both increasing AND decreasing
2) Loop through each index in the list, starting at index 1
  a) Compare the current value to the previous value
      i) If previous < current, decreasing must be False
     ii) If previous > current, increasing must be False
3) If either increasing or decreasing is still True, return True
  
```

**⚠️ Common Mistakes**

- Since you need to check the previous/next element (depending on how you write your solution), make sure your loop doesn't go out of bounds!

## I-mplement

```python
def is_monotonic(nums):
    increasing = decreasing = True

    for i in range(1, len(nums)):
        if nums[i] > nums[i-1]:
            decreasing = False
        elif nums[i] < nums[i-1]:
            increasing = False

    return increasing or decreasing
``` 

*Note: You could potentially give this function a better best-case & average-case efficiency by exiting the loop early when both `decreasing` and `increasing` are false.

However, this won't effect the worst-case efficiency (Big-O) of the solution.*