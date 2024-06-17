*[[Unit 3 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- If Teemo attack while Ashe is still poisoned, does the attack second towards the duration?
  - No.  Only count seconds when Ashe is in poison state and not being attacked.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** For each attack, check if the duration is interrupted by another attack, and add up the actual duration of each poison effect.

```markdown
1) Create an empty variable for total poisoned duration
2) For each attack time except the last one
  a) Actual duration is the smaller of: 
      - the duration input
      - the next attack time minus this attack time
  b) Add the actual duration to the total
3) The last attack will always fully complete, 
   so add one more duration to the total
4) Return total
```

**⚠️ Common Mistakes**

- Since you need to compare each attack time to the time after it, make sure your loop doesn't go out of bounds!

## I-mplement

```python
def find_poisoned_duration(time_series, duration):
    total_duration = 0
    for i in range(len(time_series)-1):
        # Calculate the actual poisoning time between two attacks
        actual_duration = min(time_series[i+1] - time_series[i], duration)
        total_duration += actual_duration
    # Add the duration of the last attack
    total_duration += duration
    return total_duration
```