*[[Unit 10 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 20 mins
* 🛠️ **Topics**: Stack, String
* 📺 **Non-TIP101 Version**: [[Valid Parentheses]]
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- What should be returned if the string is empty?
    - True, since an empty string is considered valid.

```
HAPPY CASE 1
Input: s = ""()""
Output: True
Explanation: The input string has properly matched and ordered brackets.

HAPPY CASE 2
Input: s = ""()[]{}""
Output: True
Explanation: The input string has properly matched and ordered brackets of different types.

HAPPY CASE 3
Input: s = ""(]""
Output: False
Explanation: The input string has mismatched brackets.

HAPPY CASE 4
Input: s = ""([)]""
Output: False
Explanation: The input string has brackets that are not closed in the correct order.

EDGE CASE
Input: s = """"
Output: True
Explanation: An empty string is considered valid.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

For Stack problems, we want to consider the following approaches:

- Using a stack to keep track of open brackets and ensure they are closed correctly in the correct order.
- Using a hash map to map closing brackets to their corresponding opening brackets for easy lookup.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use a stack to keep track of the last unmatched opening bracket. When a closing bracket is encountered, check if it matches the top of the stack.

```
1) Initialize an empty stack.
2) Create a mapping of closing brackets to their corresponding opening brackets.
3) Iterate through each character in the string:
    a) If the character is a closing bracket:
        i) Check if the stack is not empty and the top of the stack is the matching opening bracket.
        ii) If not, return False.
    b) If the character is an opening bracket, push it onto the stack.
4) After processing all characters, check if the stack is empty.
5) If the stack is empty, return True (all brackets were matched); otherwise, return False.
```

**⚠️ Common Mistakes**

- Not considering edge cases such as an empty string.
- Forgetting to check if the stack is empty before popping.
- Assuming that all characters in the string are brackets.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```
def is_valid(s):
    stack = []
    bracket_map = {')': '(', '}': '{', ']': '['}
    
    for char in s:
        if char in bracket_map:
            top_element = stack.pop() if stack else '#'
            if bracket_map[char] != top_element:
                return False
        else:
            stack.append(char)
    
    return not stack
```
 
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with an input to check for the expected output.
- Example: Trace with s = ""([)]""
    - Stack becomes ['(']
    - Stack becomes ['(', '[']
    - Pop '[' from stack and compare with ')', mismatch, return False

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

Assume `N` represents the length of the string `s`.

* **Time Complexity**: `O(N)` because we need to traverse all characters in the string.
* **Space Complexity**: `O(N)` in the worst case if all characters are opening brackets.