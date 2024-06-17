*[[Unit 1 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Will `n` always be a positive integer?
  - Yes.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Loop through each number less than or equal to `n`, and add it to a list if it evenly divides `n`.

```markdown
1) Create an empty list variable to store the divisors
2) Loop from 1 to `n` (inclusive)
  a) If `n` is divisible by the number, add the number to the divisors list
3) Return the divisors list
```

**⚠️ Common Mistakes**

- A number is "evenly divisible" when the remainder of the division is zero.  How can we check for that in python?

## I-mplement

```python
def find_divisors(n):
    divisors = []
    for i in range(1, n + 1):
        if n % i == 0:
            divisors.append(i)
    return divisors
```