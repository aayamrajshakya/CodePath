*[[Unit 4 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What if `n` is 1 or less?
  - The function should return `False` since 1 and any non-positive numbers do not have proper divisors that sum up to themselves.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Iterate through all numbers up to half of `n` to find its divisors, sum them, and compare the sum to `n`.

```markdown
1) Check if n is 1 or less, return False if so
2) Initialize the sum of divisors to 0
3) Loop through numbers from 1 up to n/2
  a) If a number divides n evenly, add it to the sum of divisors
4) After the loop, compare the sum of divisors to n
5) Return True if they are equal, otherwise False
```

**⚠️ Common Mistakes**

- Forgetting to exclude `n` itself from its list of divisors.
- Not handling the case when `n` is less than or equal to 1 correctly. 

## I-mplement

```python
def is_perfect_number(n):
    if n <= 1:
        return False
    sum_divisors = 0
    i = 1
    while i <= n // 2:
        if n % i == 0:
            sum_divisors += i
        i += 1
    return sum_divisors == n
```
