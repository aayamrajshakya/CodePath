*[[Unit 10 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 30 mins
* 🛠️ **Topics**: String, Two Pointers
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- How should leading zeros in the abbreviation be handled?
    - Leading zeros are not allowed and should return False if present.

```
HAPPY CASE 1
Input: word = ""substitution"", abbr = ""s10n""
Output: True
Explanation: ""s10n"" can be expanded to ""substitution"" by replacing ""ubstitutio"" with its length 10.

HAPPY CASE 2
Input: word = ""internationalization"", abbr = ""i18n""
Output: True
Explanation: ""i18n"" can be expanded to ""internationalization"" by replacing ""nternationalizatio"" with its length 18.

EDGE CASE 1
Input: word = ""substitution"", abbr = ""s010n""
Output: False
Explanation: Leading zeros are not allowed in the abbreviation.

EDGE CASE 2
Input: word = ""apple"", abbr = ""a2e""
Output: False
Explanation: ""a2e"" would expand to ""appe"" which does not match ""apple"".
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

For String problems, we want to consider the following approaches:

- Using two pointers to iterate through both the word and the abbreviation.
- Checking for digits in the abbreviation and handling them appropriately.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use two pointers to iterate through the word and abbreviation. When encountering digits in the abbreviation, convert them to a number and skip the corresponding number of characters in the word.

```
1) Initialize two pointers, word_ptr and abbr_ptr, to 0.
2) While both pointers are within the bounds of their respective strings:
    a) If the current character in abbr is a digit:
        i) Check for leading zeros and return False if present.
        ii) Convert the digit(s) to a number and move word_ptr forward by that number.
    b) If the current character in abbr is not a digit:
        i) Compare the character in word with the character in abbr.
        ii) If they do not match, return False.
    c) Move both pointers forward.
3) Return True if both pointers have reached the end of their respective strings; otherwise, return False.
```

**⚠️ Common Mistakes**

- Forgetting to handle leading zeros in the abbreviation.
- Not correctly converting multi-digit numbers in the abbreviation.
- Incorrectly updating pointers.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```
def valid_word_abbreviation(word, abbr):
    word_ptr = 0
    abbr_ptr = 0
    word_len = len(word)
    abbr_len = len(abbr)
    
    while abbr_ptr < abbr_len and word_ptr < word_len:
        if abbr[abbr_ptr].isdigit():
            if abbr[abbr_ptr] == '0':
                return False  # Leading zeros are not allowed
            num = 0
            while abbr_ptr < abbr_len and abbr[abbr_ptr].isdigit():
                num = num * 10 + int(abbr[abbr_ptr])
                abbr_ptr += 1
            word_ptr += num
        else:
            if word[word_ptr] != abbr[abbr_ptr]:
                return False
            word_ptr += 1
            abbr_ptr += 1
    
    return word_ptr == word_len and abbr_ptr == abbr_len
```
 
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with an input to check for the expected output.
- Example: Trace with word = ""substitution"", abbr = ""s10n""
    - word_ptr = 0, abbr_ptr = 0
    - 's' matches 's', move both pointers
    - abbr_ptr points to '1', calculate num = 10, move word_ptr by 10
    - word_ptr = 11, abbr_ptr = 3
    - 'n' matches 'n', move both pointers
    - Both pointers at end, return True

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

Assume `N` represents the length of the word and `M` represents the length of the abbreviation.

* **Time Complexity**: `O(N + M)` because we need to traverse both the word and the abbreviation.
* **Space Complexity**: `O(1)` because we only use a constant amount of extra space."