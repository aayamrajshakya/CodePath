*[[Unit 4 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What happens if n is negative?
  - Since by definition, prime numbers are positive numbers greater than 1, your function should return False for any n <= 1

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Check if n is less than 2, then test for factors from 2 up to the square root of n.

```markdown
1) If n is less than or equal to 1, return False (not a prime).
2) Use a loop to check divisibility from 2 up to the square root of n:
  a) If n is divisible by any number in this range, it's not a prime, return False.
  b) If no divisors are found, it's a prime, return True.
```

**⚠️ Common Mistakes**

- Forgetting that all non-prime numbers less than 2 should return False.
- Forgetting to check for divisibility by the square root of `n` 

## I-mplement

```python
def is_prime(n):
    if n <= 1:
        return False
    i = 2
    while i * i <= n:
        if n % i == 0:
            return False
        i += 1
    return True
```