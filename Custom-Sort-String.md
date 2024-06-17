*[[Unit 10 Session 2]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 20 mins
* 🛠️ **Topics**: String, Hash Map
    
## 1: U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- What should be done with characters in `s` that are not in `order`?
    - Append them to the end of the result string in any order.

```
HAPPY CASE
Input: order = "cba", s = "abcd"
Output: "cbad"
Explanation: 'c' and 'b' come first in the order, followed by 'a' and then 'd'.

HAPPY CASE
Input: order = "xyz", s = "xyzyxy"
Output: "xxxyyyzz"
Explanation: 'x' comes first, then 'y', then 'z'.

EDGE CASE
Input: order = "abc", s = "def"
Output: "def"
Explanation: None of the characters in `s` are in `order`, so the result is the same as `s`.
```

## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

For String problems, we want to consider the following approaches:

- Using a hash map to count the occurrences of each character in `s`.
- Constructing the result string based on the custom order given in `order`.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Count the occurrences of each character in `s`. Construct the result string by iterating through `order` and appending characters from `s` based on their counts. Finally, append any remaining characters from `s` that were not in `order`.

```
1) Count the occurrences of each character in `s` using a hash map `count`.
2) Initialize an empty list `result` to store the result string.
3) Iterate through each character `char` in `order`:
    a) If `char` is in `count`, append `char` repeated `count[char]` times to `result`.
    b) Remove `char` from `count`.
4) Append the remaining characters from `count` to `result`.
5) Join the `result` list into a string and return it.
```

**⚠️ Common Mistakes**

- Not correctly handling characters in `s` that are not in `order`.
- Incorrectly counting the occurrences of characters.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```
def custom_sort_string(order, s):
    # Count the occurrences of each character in s
    count = {}
    for char in s:
        if char in count:
            count[char] += 1
        else:
            count[char] = 1
    
    # Construct the result string according to the custom order
    result = []
    for char in order:
        if char in count:
            result.append(char * count[char])
            del count[char]
    
    # Append remaining characters that are not in order
    for char in count:
        result.append(char * count[char])
    
    # Join the result list into a string and return
    return ''.join(result)
```

## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with an input to check for the expected output.
- Example: Trace with order = "cba", s = "abcd"
    - count = {'a': 1, 'b': 1, 'c': 1, 'd': 1}
    - result = ['c', 'b', 'a']
    - Append 'd'
    - Join result = "cbad"

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

Assume `N` and `M` represent the lengths of `order` and `s` respectively.

* **Time Complexity**: `O(N + M)` because we need to count the characters in `s` and iterate through `order`.
* **Space Complexity**: `O(M)` because we need to store the counts of characters in `s`.