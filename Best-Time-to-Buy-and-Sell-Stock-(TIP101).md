*[[Unit 10 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Easy
* ⏰ **Time to complete**: 15 mins
* 🛠️ **Topics**: Array, Dynamic Programming
* 📺 **Non-TIP101 Version**: [[Best Time to Buy and Sell Stock]]
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- What should be returned if the prices list is empty?
    - 0, since no transaction can be made.

```
HAPPY CASE
Input: prices = [7, 1, 5, 3, 6, 4]
Output: 5
Explanation: Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit = 6-1 = 5.

HAPPY CASE 2
Input: prices = [7, 6, 4, 3, 1]
Output: 0
Explanation: In this case, no transactions are done and the max profit = 0.

EDGE CASE
Input: prices = []
Output: 0
Explanation: No prices available to make any transaction.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

For Array problems, we want to consider the following approaches:

- Using a single pass to track the minimum price and maximum profit.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Iterate through the list, keeping track of the minimum price seen so far and calculating the potential profit at each step. Update the maximum profit accordingly.

```
1) Initialize min_price to a very large number and max_profit to 0.
2) Iterate through each price in the list:
    a) Update min_price to the minimum of min_price and the current price.
    b) Calculate the current profit by subtracting min_price from the current price.
    c) Update max_profit to the maximum of max_profit and the current profit.
3) Return max_profit.
```

**⚠️ Common Mistakes**

- Not considering the case where the prices list is empty.
- Forgetting to update the minimum price correctly.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```
def max_profit(prices):
    # Initialize variables
    min_price = float('inf')
    max_profit = 0
    
    # Iterate through each price in the array
    for price in prices:
        # Update the minimum price seen so far
        min_price = min(min_price, price)
        # Calculate the potential profit
        current_profit = price - min_price
        # Update the maximum profit seen so far
        max_profit = max(max_profit, current_profit)
    
    return max_profit
```
 
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with an input to check for the expected output.
- Example: Trace with prices = [7, 1, 5, 3, 6, 4]
    - min_price = 7, max_profit = 0
    - min_price = 1, max_profit = 0
    - min_price = 1, max_profit = 4
    - min_price = 1, max_profit = 4
    - min_price = 1, max_profit = 5
    - min_price = 1, max_profit = 5

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

Assume `N` represents the number of days in the list `prices`.

* **Time Complexity**: `O(N)` because we need to traverse all prices in the list.
* **Space Complexity**: `O(1)` because we only use a constant amount of extra space.