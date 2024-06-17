## Problem Highlights

* 🔗 **Geeksforgeeks Link:**  [Leap Year]*(Insert Replit Link)
* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 5 mins
* 🛠️ **Topics**: Functions
* 🗒️ **Similar Questions**: [Welcome to CodePath](Insert Replit Link)

## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> 
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?


Given the function declaration, it tells us that we need to write a function that has one parameter. We’ll have to take in the parameter and determine if it is a leap year by using arithmetic operators. Based on the desired output, we’ll need to have one print statement.

- What arithmetic operators could we use to determine if a year is a leap year?
- What constitutes a leap year mathematically?
- Is the example output as expected?

Edge Cases: What happens is the domain of our answer (ie. what about year = 0?)
    
## 2: M-atch

**Match** what this problem looks like a function that expects a true or false return or a print statement.

(1) To determine if a year is a leap year, we will use the **modulus operator** to determine if the year is divisible by 4, 100, and 400.

(2) We will use **if statements and conditionals** to print the correct output.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.


> Since we’re being passed in the year as a parameter, we can immediately use the variable year.
> We need to check the three conditions that make a leap year. If it divisible by 4, then we should check if it is divisible by 100. If it is, then it’s not a leap year. If it is divisible by 400, then it is.
>To determine if a number is divisible by another number, we can use the modulus operator. If it is divisible, then the modulus will equal 0.
>If the year is not divisible by 4 to begin with, then we don’t need to check any other condition and can print out that it is not a leap year
>In our print statement, we would use the year variable again to print any dynamic year that was passed into the function

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def is_leap_year(year: int):
  if year % 4 == 0:
    if year % 100 != 0 or year % 400 == 0:
      print(f"{year} is a leap year.")
    else:
      print(f"{year} is not a leap year.")
  else:
        print(f"{year} is not a leap year.")

```
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with an input to check for the expected output
- Catch possible edge cases and off-by-one errors

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.
