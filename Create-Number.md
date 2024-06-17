*[[Unit 1 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- How are the digits in the list ordered?
  - They are ordered the same way you would read a number -- with the one's digit on the far right.
- What if the list is empty?
  - If the list is empty, return 0.
- Will each element in the list be between 0 and 9?
  - Yes.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Convert a list of individual digits into a number in the decimal system, using a left-to-right approach.

```markdown
1) Create a number variable and initialize to zero
2) Loop through the digits from left to right
  a) Multiply the number by 10 to create a space for a new digit
  b) Add the new digit to the number
3) Return the number

Example: [3, 9, 1]
1) number is 0
2) loop through [3, 9, 1]
   val is 3: 
       a) number times 10 is still 0
       b) number plus 3 is 3
   val is 9:
       a) number times 10 is 30
       b) number plus 9 is 39
   val is 1:
       a) number times 10 is 390
       b) number plus 1 is 391
3) return 391
```

## I-mplement

```python
def list_to_number(digits):
    number = 0
    for digit in digits:
        number = number * 10 + digit
    return number
```

Alternatively, this problem can also be solved using a right-to-left approach, but the code is slightly longer:

```python
def list_to_number(digits):
    number = 0
    place = 1 # Start at 1s place and move left
    for i in range(len(digits)-1, -1, -1):
        number = (digits[i] * place) + number
        place = place * 10
    return number
```