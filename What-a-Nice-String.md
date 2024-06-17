*[[Unit 7 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 20 mins
* 🛠️ **Topics**: Divide and Conquer, Recursion, Strings
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- Q: What should the function return if no "nice" substring exists?
  - A: If no "nice" substring exists, the function should return an empty string.

```
HAPPY CASE
Input: "YazaAay"
Output: "aAa"
Explanation: "aAa" is the longest "nice" substring.

EDGE CASE
Input: "Bb"
Output: "Bb"
Explanation: The whole string is "nice" because it contains both uppercase and lowercase 'b'.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

This problem is a variation on searching for patterns within strings, suitable for a divide and conquer approach:

- Splitting the string and finding the longest "nice" substring in each part, then comparing results.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Divide the string into halves, recursively find the longest "nice" substring in each half, and return the longest of them.

```markdown
1) Check if the current string segment is "nice."
2) If not, split the string in half.
3) Recursively find the longest "nice" substring in each half.
4) Return the longer of the two "nice" substrings.
```

**⚠️ Common Mistakes**

- Overlooking substrings that cross the middle of the string segment.
- Not correctly identifying all characters in both cases (upper and lower).

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```python
def is_nice(sub):
    """ Check if the substring 'sub' is nice, i.e., contains both uppercase and lowercase of each letter. """
    lower_count = {}
    upper_count = {}
    
    # Count lowercase and uppercase letters
    for char in sub:
        if 'a' <= char <= 'z':
            if char in lower_count:
                lower_count[char] += 1
            else:
                lower_count[char] = 1
        elif 'A' <= char <= 'Z':
            if char in upper_count:
                upper_count[char] += 1
            else:
                upper_count[char] = 1
    
    # Check if for every lowercase letter there is an uppercase version and vice versa
    for char in lower_count:
        upper_char = char.upper()
        if upper_char not in upper_count:
            return False
    
    for char in upper_count:
        lower_char = char.lower()
        if lower_char not in lower_count:
            return False

    return True

def longest_nice(ss):
    """ Recursive function to find the longest nice substring in 'ss'. """
    if len(ss) < 2:
        return ""
    if is_nice(ss):
        return ss
    mid = len(ss) // 2
    left = longest_nice(ss[:mid])
    right = longest_nice(ss[mid:])
    if len(left) >= len(right):
        return left
    else:
        return right

def longest_nice_substring(s):
    """ Main function to initialize the recursive search for the longest nice substring. """
    if len(s) < 2:
        return ""
    return longest_nice(s)
```

Alternative solution taking advantage of Python:

```python
def is_nice(s):
    return set(s.lower()) == set(s.upper()) and set(s.lower()) == set([char.lower() for char in s if char.isalpha()])

def longest_nice_substring(s):
    if not s:
        return ""
    if is_nice(s):
        return s
    left = longest_nice_substring(s[:len(s)//2])
    right = longest_nice_substring(s[len(s)//2:])
    return max(left, right, key=len)
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Test the function with input "YazaAay" to ensure it returns "aAa".
- Validate with input "Bb" to confirm it returns "Bb" as expected.

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

* **Time Complexity**: Potentially O(n^2) in the worst case, depending on the distribution of characters and the length of the string as the entire string is checked at each recursion level.
* **Space Complexity**: O(n) for the recursion stack, especially if the recursion depth approaches the length of the string.
