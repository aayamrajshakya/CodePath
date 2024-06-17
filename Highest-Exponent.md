*[[Unit 4 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What if the base is 1?
  - The exponent can be indefinitely large as any power of 1 is still 1. Handling this edge case is important.
- What if the limit is less than the base?
  - The highest exponent should be 0, as any positive exponent would exceed the limit.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Start with the smallest exponent and multiply the base until the result exceeds the limit.

```markdown
1) Initialize `exponent` to 0, representing the smallest exponent.
2) Initialize `power` to 1, which is base^0.
3) While multiplying the current `power` by the base stays within the `limit`:
  a) Multiply `power` by `base` to get the next power.
  b) Increment `exponent` by 1 to reflect the next higher power level.
4) Once the loop exits, `exponent` will be one less than the number of successful multiplications, so return it.
```

**⚠️ Common Mistakes**

- Forgetting to handle edge cases where `base` is 1 or `limit` is less than `base`.
- Incorrectly updating the `power` or misplacing the increment of `exponent`.

## I-mplement

```python
def find_highest_exponent(base, limit):
    exponent = 0  # Start with an exponent of 0
    power = 1  # The result of base^exponent
    while power * base <= limit:
        power *= base
        exponent += 1  # Increment the exponent each time the base is multiplied
    return exponent
```