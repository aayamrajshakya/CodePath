*[[Unit 10 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 30 mins
* 🛠️ **Topics**: String, Greatest Common Divisor (GCD)
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- What should be returned if one of the strings is empty?
    - Return the other string since any string divides an empty string.

```
HAPPY CASE
Input: str1 = "ABCABC", str2 = "ABC"
Output: "ABC"
Explanation: "ABC" is the largest string that divides both "ABCABC" and "ABC".

HAPPY CASE 2
Input: str1 = "ABABAB", str2 = "ABAB"
Output: "AB"
Explanation: "AB" is the largest string that divides both "ABABAB" and "ABAB".

EDGE CASE
Input: str1 = "LEET", str2 = "CODE"
Output: """"
Explanation: There is no common divisor string that divides both ""LEET"" and ""CODE"".
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

For String problems, we want to consider the following approaches:

- Using the concept of the Greatest Common Divisor (GCD) to find the largest common divisor of the lengths of the two strings.
- Checking if a substring of the appropriate length divides both strings.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use the GCD of the lengths of the two strings to find the largest possible divisor string. Check if this string divides both `str1` and `str2`.

```
1) Define a helper function `is_divisible(s, t)` that checks if string `t` divides string `s`.
2) Find the GCD of the lengths of `str1` and `str2`.
3) Use the GCD length to extract a candidate substring from `str1`.
4) Check if this candidate substring divides both `str1` and `str2`.
5) Return the candidate substring if it divides both strings; otherwise, return an empty string.
```

**⚠️ Common Mistakes**

- Not correctly handling cases where there is no common divisor.
- Incorrectly calculating the GCD or checking divisibility.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```
def gcd_of_strings(str1, str2):
    def is_divisible(s, t):
        if len(s) % len(t) != 0:
            return False
        repeat = len(s) // len(t)
        return t * repeat == s

    def gcd(a, b):
        while b:
            a, b = b, a % b
        return a
    
    gcd_length = gcd(len(str1), len(str2))
    candidate = str1[:gcd_length]
    
    if is_divisible(str1, candidate) and is_divisible(str2, candidate):
        return candidate
    return ""
```
 
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with an input to check for the expected output.
- Example: Trace with str1 = "ABCABC", str2 = "ABC"
    - gcd_length = gcd(6, 3) = 3
    - candidate = "ABC"
    - is_divisible("ABCABC", "ABC") -> True
    - is_divisible("ABC", "ABC") -> True
    - Return ""ABC""

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

Assume `N` represents the length of the shorter string.

* **Time Complexity**: `O(N)` because we need to check divisibility and find the GCD of the lengths.
* **Space Complexity**: `O(1)` because we only use a constant amount of extra space.